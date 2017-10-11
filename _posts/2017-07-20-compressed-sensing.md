---
layout: post
title: "压缩感知"
author: "李军"
categories: journal
tags: [RMT, compressed sensing, harmonic analysis]
image:
  feature: 
  teaser: 
  credit: 
  creditlink: ""
---

本文概述了压缩感知的基本知识与应用。

## 理论

+ David Donoho[^1]
+ Candes，Tao
+ JA Tropp[^2]
+ L1范数
+ 基追踪

## 应用
下面代码在Julia 0.6.0环境下测试通过
### 信号压缩

#### 基追踪

```julia
using MathProgBase
function BP_linprog(s,Φ) 
    #   Detailed explanation goes here  
    #   s = Φ * α (α is a sparse vector)    
    #   Given s & Φ, try to derive α     
    p = size(Φ,2); 
    q = size(Φ,1);
    #according to section 3.1 of the reference  
    c = ones(2*p);
    A_aug = zeros(q,2*p);
    #A_aug = [Φ,-Φ];
    for j=1:p
        A_aug[:,j] = Φ[:,j]
        A_aug[:,j+p] = -Φ[:,j]
    end 
    b = s;  
    #lb = zeros(2*p);  
    x0 = linprog(c,A_aug,'<',b);
    x0 = x0.sol;
    α = x0[1:p] - x0[p+1:2*p];  
    return α
end  
```

#### 重构算法
```julia
using Plots
M = 64;#观测值个数(M>=K*log(N/K),至少40,但有出错的概率)    
N = 256;#信号x的长度    
K = 7;#信号x的稀疏度    
Index_K = randperm(N);    
x = zeros(N);    
x[Index_K[1:K]] = 5*randn(K);#x为K稀疏的，且位置是随机的  
#f1=50;    #  信号频率1  
#f2=100;   #  信号频率2  
#f3=200;   #  信号频率3  
#f4=400;   #  信号频率4  
#fs=800;   #  采样频率  
#ts=1/fs;  #  采样间隔  
#  采样序列Ts  
#  完整信号,由4个信号叠加而来  
#x=[0.3*cos(2*pi*f1*Ts*ts)+0.6*cos(2*pi*f2*Ts*ts)+0.1*cos(2*pi*f3*Ts*ts)+0.9*cos(2*pi*f4*Ts*ts) for Ts=1:N];  

#Ψ = eye(N);#x本身是稀疏的，定义稀疏矩阵为单位阵x=Ψ*θ 
# 我们将会采用wavelet变换来修正
Ψ=fft(eye(N))/√N;
Φ = randn(M,N);#测量矩阵为高斯矩阵    
A = real(Φ * Ψ);#传感矩阵    
y = Φ * x;#得到观测向量y  
#plot([y,x],label=[:y,:x],linestyle=[:dot,:solid]);#绘出y信号&原信号x
# 恢复重构信号x       
θ = BP_linprog(y[:],A);    
x_r = real(Ψ * θ);# x=Ψ * θ       
# 绘图        
plot([x,y,x_r],linestyle=[:solid,:dot,:dashdot]);#绘出原信号x & 观测信号y & x的恢复信号x_r
#legend('Recovery','Original')
```

#### 误差项
```julia
println("\n恢复残差：");    
norm(x_r-x)#恢复残差 
```

### 图像压缩


## 参考文献
[^1]: Chen S S, Donoho D L, Saunders M A. Atomic decomposition by basis pursuit. SIAM review, 2001, 43(1): 129-159.
[^2]: Joel A. Tropp and Anna C. Gilbert, Signal Recovery From Random Measurements Via Orthogonal Matching Pursuit，IEEE TRANSACTIONS ON INFORMATION THEORY, VOL. 53, NO. 12, DECEMBER 2007.

