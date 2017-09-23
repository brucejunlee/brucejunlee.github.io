---
layout: post
title: "Julia编程(一): 入门"
author: "李军"
categories: journal
tags: [Julia, data science]
image:
  feature: juliabasics.jpg
  teaser: juliabasics-teaser.jpg
  credit:
  creditlink:
---

想通过短篇幅的一篇文章将一种语言讲全讲透是很难的，因此这里我将跳过大多数语言共有的特性和元素，着重讲述Julia独有的一些性质。本文是Julia编程系列的第一篇文章，后面将不定期推出Julia的后续教程，着重讲述它在通用计算，金融分析，高性能计算，数据科学，机器学习，深度学习等方面的应用。



### 引言

现代语言设计和编译技术能够尽量消除性能妥协，提供一种单一的高产出、高效的环境来构建原型并部署高性能的应用。<b>Julia</b> 语言正扮演着这种角色，它是一种灵活的动态编程语言，非常适用于科学计算和数值计算，并且性能和传统静态类型的语言相当。	

Julia编译器不同于`Python`，`R`这类语言中使用的解释器。如果我们理解Julia的工作原理，我们将很容易写出接近于C语言速度的代码。

Julia提供了可选类型和多指派等特性，利用类型推断和<b>LLVM</b>实现的即时编译(<b>Just-In-Time</b>)技术来达到高性能，并结合了过程式、函数式和面向对象编程的多种特性。Julia，同R、`MATLAB`、Python等语言一样，为高级数值计算提供了简易操作和丰富的表达能力，同时还支持泛化编程。为此，Julia构建在数学语言之上，并借鉴了`Lisp`，`Perl`，Python，`Lua`，`Ruby`等动态语言特性。

Julia作为类型动态语言存在一些重要特性：

* 极小的内核部分。标准库采用Julia自身编写，包括整数运算等最基本的操作
* 是一种丰富的类型语言，可用于构造对象，描述对象，同时可用于类型声明
* 通过<b>多指派</b>(<b>multi-dispatch</b>)在不同参数类型组合上来定义函数行为
* 不同参数类型代码的自动生成
* 高性能，可以达到C一类的静态编译语言的性能

在大多数动态语言中没有类型声明，因此人们不能向编译器指明参数类型，也不能对类型本身进行操作。另一方面，在静态语言中，通常必须向编译器声明类型，类型只存在于编译时，而在运行时无法操纵。在Julia语言中，类型本身就是运行时对象，同时可以将信息传送给编译器。

类型和多指派是统一于Julia的内核特性：函数定义在参数类型的不同组合上，并通过指派来应用。这与数学语言相匹配，因为传统面向对象指派中的第一个参数是很不自然的。算符仅仅是一类特殊标记的函数。

由于运行时类型推断和对性能的持续关注，Julia计算上的性能远超其它动态语言，甚至与静态编译语言不相上下。我们知道，对于大规模数值计算问题，速度一直，并且可能持续，是最关键的考虑标准：过去几十年，用于处理的数据量已经很轻松地赶上了摩尔定律。

Julia语言的目的是将易用性、能力和高效性融合在一种语言中，除此之外，Julia还包含一些重要的优势:

+  免费开源（MIT许可证）

+  用户定义的类型与内置类型一样的紧凑迅捷

+  去向量化

+  并行计算，分布式计算

+  轻量线程（<b>协程coroutines</b>）

+  类型系统

+  数值类型和其它类型之间的转换以及类型晋升

+  <b>UTF-8</b>等Unicode支持

+  直接调用C函数，无须封装或API

+  类shell操作

+  类Lisp宏，元编程(<b>metaprogramming</b>)

   ​

### 安装

+ <b>REPL</b>(read-eval-print-loop)

  + 我们可以直接从[官网](http://julialang.org/downloads/)下载对应的预编译二进制文件或者从源码编译安装

  + 打开方式

    + 直接点击桌面图标打开

    + 将julia安装路径添加到.bash_profile文件中，然后可以在Terminal直接输入julia进入开发环境

      ```shell
      julia
      ```

+ <b>IJulia</b> notebook

+ Juno

+ JuliaPro

+ Atom/Sublime中安装插件

  ​

### 代码执行

+ 终端输入

  ```julia
  julia script.jl arg1 arg2 ...
  ```

+ Julia环境下

  ```julia
  include("script.jl")
  ```

  ​

### 变量

+ UTF-8编码: 如\pi-tab, \delta-tab, \alpha-tab-\hat-tab-\\_2-tab

  ```julia
  δ = 0.00001
  ```

+ 命名：除了内置语句中保留的关键字外

+ 风格习惯

  + 小写


  + 词分隔用下划线\_ （不鼓励使用）

  + 类型名和模块名开始于大写字母，词分隔采用驼峰法

  + 函数名和宏名采用无下划线的小写形式

  + 有实参的函数可以以!结尾，这些被称为可变(in-place)函数

    ​

### 数值

+ 类型

  + 整数类型
    + Int8, UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64, Int18, UInt128, Bool(8位)
    + 无符号整型是以0x前缀的16进制数0-9a-f
    + 当然二进制(0b)和8进制(0o)也是支持的

  + 浮点数类型

    * IEEE754
    * Float16(半精度), Float32(单精度), Float64(双精度)
    * 16进制对于浮点数也是有效的，但输出只是Float64
    * 浮点数有两个零，分别是0.0和-0.0
    * 特殊值
      * Inf16, -Inf16, NaN16
      * Inf32, -Inf32, NaN32
      * Inf, -Inf, NaN

  + 复数

    ```julia
    c = 1 + 2im
    real(c)
    imag(c)
    conj(c)
    abs(c)    # c到0的距离
    abs2(c)
    angle(c)  # 以弧度形式返回相角

    a = 1; b = 2;
    complex(a, b)
    ```

  + 有理数

    ```julia
    a = 2; b = 3;
    num(a // b)
    den(a // b)

    float(a // b)
    ```




  + 操作符

    + 位运算
      + 非～，与&， 或\|， 异或\$， 逻辑右移\>\>\>， 算术右移\>\>， 逻辑/算术左移\<\<
    + 数值比较
      + ==， !=或者≠， <， <=或者≤， >， >=或者≥

+ 函数

  + Sys.WORD_SIZE：返回操作系统的位数

  + typeof: 参数是具体数值

  + typemin, typemax: 参数是值类型

  + BigInt, BigFloat: 输入是上一条函数输出

  + sizeof:参数是具体数值

  + eps: 参数是类型或数值

  + zero, one: 参数是类型或数值

  + isa

    ```julia
    x = 1
    isa(x, Int)
    ```

  + prevfloat, nextfloat:参数是具体数值

  + setrounding: 参数是类型，选项是RoundUp, RoundDown, RoundNearest

    ```julia
    x = 1.1; y = 0.1;
    setrounding(Float64, RoundDown) do
      x + y
    end
    ```

  + parse: 参数是可转化为数值的抽象字符串，输出是对应数值

  + factorial：阶乘

  + 比较函数:

    + isequal, isfinite, isinf, isnan

  + setprecision

  + 舍入操作

    + round(x), round(T, x)
    + floor(x), floor(T, x)
    + ceil(x), ceil(T, x)
    + trunc(x), trunc(T, x)

  + 除法

    + div, fld, cld, rem, mod, mod1, mod2pi, divrem, fldmod, gcd(x, y…), lcm(x, y...)

  + 按元操作:

    ```julia
    x = [1, 2, 3, 4]
    sin.(x)
    ```

  + 三角函数

    + sinpi(x), cospi(x): 精确计算sin(pi\*x), cos(pi\*x)
    + atan2: 计算x轴与指定参数点之间的弧度
    + sind(x): x以度数给定

  + 指数函数

    * 平方根sqrt, 立方根cbrt, 直角三角形弦长hypot(x, y)
    * 当x接近0时exp(x) - 1的值，expm1(x)
    * 当x接近0时log(1 + x)的值，log1p(x)

  + 特殊函数: 在Julia0.6以后，特殊函数放在SpecialFunctions包中，需要安装

    ```julia
    Pkg.add("SpecialFunctions")
    using SpecialFunctions
    ```

    + erf, erfc: erfc是erf补函数
    + digamma:对数gamma函数lgamma的导数
    + airy(z), airy(1, z), airy(2, z), airy(3, z), airy(k, z)


+ 类型晋升(promotion)


+ 类数学表达式

  ```julia
  x = 3
  2x^2 - 3x + 1
  2^2x
  (x - 1)x
  (x - 1)(x + 1)  # wrong
  x(x + 1)        # wrong
  ```




### 字符串

+ Char：类似C和Java，在Julia中Char作为最高等级的类型

  * 32位

  * ```julia
    x = 'x'
    typeof(x)
    Int('x')    # output: 120
    Char(120)   # output: 'x'
    ```

  * Unicode字符包括\\u后面至多四位16进制数或\\U后面至多八位16进制数

  * 并非每个整数都是合法的Unicode编码，合法的Unicode编码包括U+00～U+d7ff，U+e000～U+10ffff

    ```julia
    Char(0x110000)
    isvalid(Char, 0x110000)
    ```

    ​

+ String: 在Julia0.6之前，采用AbstractString

  + 不可变

  + 偏函数：从索引到字符的映射

  + 不同于Python，Julia第一个索引从1开始，最后一个索引可以用*end*表示，*end*可以参与运算

    ```julia
    str = "Hello, World!\n"
    str[1]
    str[end]
    str[end - 1]
    str[end÷2]
    ```

    ​

  + 索引结果是字符，切片结果是字符串

    ```julia
    str[6]
    str[6:6]
    ```

    ​

  + 并非所有索引都有效, 我们用nextind(s, 1), nextind(s, 4)来计算下标

    ```julia
    s = "\u2200 x \u2203 y"
    s[1]
    s[2]  # wrong
    s[4]
    ```


  + length(s)<=endof(s)=sizeof(s)，所以我们采用如下方式高效迭代字符串

    ```julia
    for c in s
      println(c)
    end
    ```

  + 字符串插入

    ```julia
    a = "Hello"
    b = "World"
    string(a, ", ", b, "!\n")
    "$a, $b!\n"
    "1 + 2 = $(1 + 2)"
    ```

  * 特殊字符串

    + VERSION

  * 常见函数

    * search(string, char)
    * search(string, char, offset)
    * contains(string, substring)
    * in()
    * start(string)
    * next(string, index)
    * repeat(string, number)
    * join(string-array, ", ", " and ")
    * ind2chr(string, index)
    * chr2ind(string, index)

    ​


#### 正则表达式





#### 列表／集合／字典





#### 数组／矩阵





#### 函数



#### 互操作性

​	其它语言调用



#### 类型，多指派





### 宏





### 元编程





### 示例












































