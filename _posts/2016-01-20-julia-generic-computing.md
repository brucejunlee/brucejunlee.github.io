---
layout: post
title: "Julia编程(二): 通用计算"
author: "李军"
categories: journal
tags: [Julia, HPC]
image:
  feature: juliabasics.jpg
  teaser: juliabasics-teaser.jpg
  credit:
  creditlink:
---

本文是Julia编程系列的第二篇文章，着重讲述在几个通用计算方面的应用，如网络，并行[^1]，日期等，关于最新用法和变更请查看[在线文档](https://docs.julialang.org/en/stable/index.html)。

## 1 网络&流

### 1.1 基本I/O流

```julia
write(STDOUT, "Hello World"); # suppress return value 11 with ;

read(STDIN, Char)
read(STDIn, 4)

x = zeros(UInt8, 4)
read!(STDIN, x)

readline(STDIN) # read the entire line instead

for line in eachline(STDIN) 
  println("Found $line")
end

while !eof(STDIN)
  x = read(STDIN, Char)
  println("Found: $x")
end
```

### 1.2 文本I/O

```julia
write(STDOUT,0x61); # suppress return value 1 with ;

print(STDOUT, 0x61)
# or show()
```

### 1.3 文件流

```julia
f = open("hello.txt")
readlines(f)

f = open("hello.txt", "w")
write(f, "Hello again.")
close(f) # IOStream must be closed before the write is actually flushed to disk
```

```julia
function read_and_capitalize(f::IOStream) 
  return uppercase(readstring(f))end
open(read_and_capitalize, "hello.txt")

# equivalent
open("hello.txt") do f
  uppercase(readstring(f))
end
```

### 1.4 TCP套接字(socket)

```julia
@async begin  server = listen(2000)  while true
    sock = accept(server)
    println("Hello World\n")
  end 
end

julia> listen(2000)  # Listens on localhost:2000 (IPv4)
julia> listen(ip"127.0.0.1", 2000) # Equivalent to the first
julia> listen(ip"::1", 2000) # Listens on localhost:2000 (IPv6)
julia> listen(IPv4(0), 2001) # Listens on port 2001 on all IPv4 interfaces
julia> listen(IPv6(0), 2001) # Listens on port 2001 on all IPv6 interfaces
julia> listen("testsocket")  # Listens on a UNIX domain socket/named pipe

julia> accept(2000)
julia> connect(2000)

@async begin  server = listen(2001)  while true
    sock = accept(server)
    @async while isopen(sock)
      write(sock,readline(sock))	end
  endend

julia> clientside = connect(2001)

@async while true
  write(STDOUT,readline(clientside))end

julia> println(clientside,"Hello World from the Echo Server")
julia> close(clientside)
```

### 1.5 解析IP地址

+ connect(host::String, port)

```julia
julia> connect("google.com", 80)
julia> getaddrinfo("google.com")
```

## 2 并行计算

大多数现代计算机拥有多块CPU，一个集群可以组合几个计算机。有两个主要因素影响性能，一个是CPU自身的速度，其次是内存访问的速度。Julia基于消息传递来提供多进程环境，使得程序能够一次在不同内存区的多进程中运行。

Julia消息传递机制的实现不同于MPI等其它环境。Julia通信通常是单边的(one-sided)，即在两进程操作中，程序员只需要精确管理一个进程。

Julia并行计算内置在两个原语上，即

+ remote references：Future，RemoteChannel
+ remote calls：wait，fetch

```shell
$ julia -p 2
```

```julia
addprocs(3)
```

```julia
r = remotecall(rand, 2, 2, 2)
s= @spawnat 2 1 .+ fetch(r)
fetch(s)

# equivalent
remotecall_fetch(getindex, 2, r, 1, 1)

r = @spawn rand(2, 2)
s = @spawn 1 .+ fetch(r)
fetch(s)
```

### 2.1 包加载

+ include只能将文件加载到单个进程中，using使得模块被加载到所有进程中。
+ 强制操作：@everywhere
+ 预加载：

```shell
$ julia -p <n> -L file1.jl -L file2.jl driver.jl
```

+ 每个进程都有标识符：提供交互式环境的进程id=1即master进程，而默认并行操作的进程被称为`workers`；当只有一个进程时，进程1被当作工作进程，否则工作进程是所有非1的进程
+ --machinefile选项
+ addprocs，rmprocs，workers

### 2.2 数据运动

```julia
A = rand(1000, 1000) # constructed locally
Bref = @spawn A^2    # sent to another process where it is squared
fetch(Bref)

Bref = @spawn rand(1000, 1000)^2  # both constructed and squared on another process, so send much less data than the first
fetch(Bref)
```

### 2.3 并行map／loop

```julia
function count_heads(n) 
  c::Int = 0  for i=1:n
    c += rand(Bool)  end
  cend

julia> @everywhere include("count_heads.jl")julia> a = @spawn count_heads(100000000)julia> b = @spawn count_heads(100000000)julia> fetch(a)+fetch(b)
```

并行for-loop中迭代没有按特定顺序发生，因为迭代运行在不同进程中，所以对变量和数组的写操作不是全局可见的。并行循环中用到的任何变量都将被复制广播到每个进程中。如果只用于读取变量，那么使用并行循环外的变量是可以的。

```julia
nheads = @parallel (+) for i=1:200000000
  Int(rand(Bool))end
```

```julia
# not work
a = zeros(100000) 
@parallel for i=1:100000  a[i] = i 
end

# work
a = SharedArray(Float64,10) 
@parallel for i=1:10  a[i] = i 
end
```

我们可以扔掉reduce操作，这时循环将异步进行，当然我们可以强制同步执行

+ 用于小的迭代计算：@sync @parallel for
+ 每次函数调用需要完成大量工作：pmap

```julia
M = Matrix{Float64}[rand(1000, 1000) for i = 1:10]
pmap(svd, M)
```

### 2.4 调度

Julia并行计算使用Task在多个计算间进行切换。当代码进行fetch，wait等通信时，当前任务被挂起，调度器挑选另一个任务运行。当等待的事件完成时重启任务。

+ dynamic scheduling

```julia
function pmap(f, lst)
  np = nprocs() # determine the number of processes available 
  n = length(lst)
  results = Vector{Any}(n)
  i=1
  # function to produce the next work item from the queue.
  # in this case it's just an index.
  nextidx() = (idx=i; i+=1; idx)
  @sync begin
    for p=1:np
      if p != myid() || np == 1
        @async begin 
          while true
            idx = nextidx() 
            if idx > n
              break 
            end
            results[idx] = remotecall_fetch(f, p, lst[idx]) 
          end
        end 
      end
    end 
  end
  resultsend
```

### 2.5 信道

信道提供了一种快速的任务内通信方式。

+ Channel{T}(n::Int)
+ 读：fetch, take!
+ 写：put!
+ isready
+ wait
+ close

### 2.6 共享数组

使用系统共享内存将同一个数组映射到许多进程中。

```julia
SharedArray(T::Type, dims::NTuple; init=false, pids=Int[])
```

与分布式数组DArray的异同：

+ 在DArray中，每个进程只能局部访问一块数据，没有两个进程共享同一块
+ 在SharedArray中，每个参与其中的进程都可以访问整个数组
+ sdata()

```julia
# This function retuns the (irange,jrange) indexes assigned to this worker@everywhere function myrange(q::SharedArray) 
  idx = indexpids(q)
  if idx == 0
    # This worker is not assigned a piece
    return 1:0, 1:0 
  end
  nchunks = length(procs(q))
  splits = [round(Int, s) for s in linspace(0,size(q,2),nchunks+1)] 
  1:size(q,1), splits[idx]+1:splits[idx+1]end# Here's the kernel@everywhere function advection_chunk!(q, u, irange, jrange, trange)
  @show (irange, jrange, trange) # display so we can see what's happening 
  for t in trange, j in jrange, i in irange
    q[i,j,t+1] = q[i,j,t] + u[i,j,t] 
  end
  qend# Here's a convenience wrapper for a SharedArray implementation@everywhere advection_shared_chunk!(q, u) = advection_chunk!(q, u, myrange(q)..., 1:size(q,3)-1)

advection_serial!(q, u) = advection_chunk!(q, u, 1:size(q,1), 1:size(q,2), 1:size(q,3)-1)

function advection_parallel!(q, u) 
  for t = 1:size(q,3)-1
    @sync @parallel for j = 1:size(q,2) 
      for i = 1:size(q,1)
        q[i,j,t+1]= q[i,j,t] + u[i,j,t] 
      end
    end 
  end
  qend

function advection_shared!(q, u) 
  @sync begin
    for p in procs(q)
      @async remotecall_wait(advection_shared_chunk!, p, q, u)
    end 
  end
  qend

# $ julia -p 4

q = SharedArray(Float64, (500,500,500)) 
u = SharedArray(Float64, (500,500,500))
# Run once to JIT-compileadvection_serial!(q, u)advection_parallel!(q, u)advection_shared!(q,u)julia> @time advection_serial!(q, u);
julia> @time advection_parallel!(q, u);
julia> @time advection_shared!(q,u); # best
```

### 2.7 集群管理

+ LocalManager
+ SSHManager 
+ connect
+ kill

### 2.8 其它

网络拓扑和多线程目前在Julia中还处于实验阶段

#### network topology

+ addprocs的关键字参量topology
+ :all\_to\_all
+ :master\_slave
+ :custom

#### multi-threading

+ Threads.nthreads()
+ export JULIA_NUM_THREADS = 4: 在Windows命令行或Linux／OSX平台的Cshell上，将export改为set
+ Threads.threadid()
+ @threads
+ @threadall

## 3 日期&时间

Date和DateTime是Dates模块中的两种类型，分别表示day和millisecond精度。它们不考虑时区影响，或者说它们是本地时间。额外的时区功能通过TimeZones.jl包添加。

### 3.1 构造器

```julia
DateTime(2013)
DateTime(2013, 7)
DateTime(2013, 7, 1)
DateTime(2013, 7, 1, 12)
DateTime(2013, 7, 1, 12, 30)
DateTime(2013, 7, 1, 12, 30, 59)
DateTime(2013, 7, 1, 12, 30, 59, 1)

Date(2013)
Date(2013, 7)
Date(2013, 7, 1)
Date(Dates.Year(2013), Dates.Month(7), Dates.Day(1))
Date(Dates.Month(7), Dates.Year(2013))

Date("2015-01-01","y-m-d")
DateTime("20150101","yyyymmdd")
```

+ 支持文本形式的月份解析，u对应于Jan，Feb，Mar等；U对应于January，February，March等；这和dayname，monthname等name=>value映射相似。

高效的日期解析

```julia
df = Dates.DateFormat("y-m-d");
dt = Date("2015-01-01",df)
dt = Date("2015-01-02",df)
```

### 3.2 时间段

```julia
dt = Date(2012, 2, 29)
dt2 = Date(2000, 2, 1)

dump(dt)  # UTInstant{Day}
dump(dt2)

dt > dt2  # true
dt != dt2  # true

dt + dt2  # operation not defined for TimeTypes
dt * dt2  # operation not defined for TimeTypes
dt / dt2  # operation not defined for TimeTypes

dt - dt2  # 4411 days
dt2 - dt

# but
y1 = Dates.Year(1)
y2 = Dates.Year(2)
y3 = Dates.Year(10)

y1 + y2
div(y3, y2)
y3 - y2
y3 * y2  # error
y3 * 20
y3 % y2
y1 + 20  # error
div(y3, 3)

dt = DateTime(2012, 2, 29)
dt2 = DateTime(2000, 2, 1)

dump(dt)  # UTInstant{Millisecond}

dt - dt2  # 381110402000 milliseconds
```

### 3.3 访问(accessor)函数

```julia
t = Date(2016, 1, 20)
Dates.year(t)  # 2016
Dates.month(t)
Dates.week(t)  # 3
Dates.day(t)

Dates.Year(t)  # 2016 years
Dates.Day(t)  # 20 days

Dates.yearmonth(t)
Dates.monthday(t)
Dates.yearmonthday(t)

dump(t)
t.instant

Dates.value(t)
```

### 3.4 查询(query)函数

```julia
t = Date(2016, 1, 20)
Dates.dayofweek(t)  # 3
Dates.dayname(t)  # "Wednesday"
Dates.dayofweekofmonth(t)  # 3

Dates.monthname(t)  # "January"
Dates.daysinmonth(t)  # 31

Dates.isleapyear(t)  # true
Dates.dayofyear(t)  # 20
Dates.quarterofyear(t)  # 1
Dates.dayofquarter(t)  # 20
```

dayname()和monthname()方法可以取可选关键字locale，返回在其它语言区那一年的那一天或那一月的名字，Julia 0.6.0版本取消了VALUETODAYOFWEEK, VALUETOMONTH。

```julia
french_months = ["janvier", "février", "mars", "avril", "mai", "juin", "juillet", "août", "septembre", "octobre", "novembre", "décembre"]
french_monts_abbrev = ["janv","févr","mars","avril","mai","juin", "juil","août","sept","oct","nov","déc"]
french_days = ["lundi","mardi","mercredi","jeudi","vendredi","samedi","dimanche"]
Dates.LOCALES["french"] = Dates.DateLocale(french_months, french_monts_abbrev, french_days, [""])
Dates.dayname(t;locale="french")
Dates.monthname(t;locale="french")
Dates.monthabbr(t;locale="french")
```

### 3.5 日历算术

```julia
(Date(2014,1,29)+Dates.Day(1)) + Dates.Month(1)
(Date(2014,1,29)+Dates.Month(1)) + Dates.Day(1)

Date(2014,1,29) + Dates.Day(1) + Dates.Month(1)
```

### 3.6 适配器(adjuster)

```julia
Dates.firstdayofweek(Date(2014,7,16))
Dates.lastdayofmonth(Date(2014,7,16))
Dates.lastdayofquarter(Date(2014,7,16))

istuesday = x->Dates.dayofweek(x) == Dates.Tuesday
Dates.tonext(istuesday, Date(2014,7,13))
Dates.tonext(Date(2014,7,13), Dates.Tuesday)  # equivalent

Dates.tonext(Date(2014,7,13)) do x  # Return true on the 4th Thursday of November (Thanksgiving) 
  Dates.dayofweek(x) == Dates.Thursday && 
  Dates.dayofweekofmonth(x) == 4 && 
  Dates.month(x) == Dates.Novemberend
```

filter通过取开始和结束日期将适配过程向量化(还可以详述StepRange), Julia 0.6.0取消了recur函数

```julia
dr = Dates.Date(2014):Dates.Date(2015)
filter(dr) do x
  Dates.dayofweek(x) == Dates.Tue && 
  Dates.April <= Dates.month(x) <= Dates.Nov && 
  Dates.dayofweekofmonth(x) == 2end
```

### 3.7 舍入

```julia
floor(Date(1985, 8, 16), Dates.Month)
ceil(DateTime(2013, 2, 13, 0, 31, 20), Dates.Minute(15))
round(DateTime(2016, 8, 6, 20, 15), Dates.Day)

round(DateTime(2016, 7, 17, 11, 55), Dates.Hour(10))
round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Hour(2))
round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Minute(2))
round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Month(2))
```

## 4 运行外部程序

```julia
julia> run(`echo hello`)
julia> run(`echo hello` & `echo world`) # the order of the output here is non-deterministic because the two echo processes are started nearly simultaneously
julia> run(pipeline(`echo hello`, `sort`))

a = readstring(`echo hello`)
chomp(a) = "hello"
```

## 5 调用C和Fortran代码

```julia
t = ccall( (:clock, "libc"), Int32, ())

path = ccall((:getenv, "libc"), Cstring, (Cstring,), "SHELL")
unsafe_string(path)
```

### 5.1 C兼容的函数指针

```julia
function mycompare{T}(a::T, b::T)  return convert(Cint, a < b ? -1 : a > b ? +1 : 0)::Cintend
const mycompare_c = cfunction(mycompare, Cint, (Ref{Cdouble}, Ref{Cdouble}))
```

### 5.2 C类型映射到Julia

+ cconvert
+ unsafe_convert

## 6 嵌入Julia代码

```c
#include <julia.h>int main(int argc, char *argv[]) {    /* required: setup the Julia context */jl_init(NULL);/* run Julia commands */    jl_eval_string("print(sqrt(2.0))");    /* strongly recommended: notify Julia that the         program is about to terminate. this allows         Julia time to cleanup pending write requests         and run all finalizers*/    jl_atexit_hook(0);return 0; }
```

[^1]: Jeff Bezanson, Stefan Karpinski, Viral Shah, Alan Edelman, et al., Julia Language Documentation(Release 0.6.0-dev).
