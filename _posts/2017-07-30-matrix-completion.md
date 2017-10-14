---
layout: post
title: "矩阵补全(一): 简介"
author: "李军"
categories: journal
tags: [RMT, matrix completion]
image:
  feature: 
  teaser: 
  credit: 
  creditlink: ""
---

本文概述了矩阵补全的基本知识与应用。

## 理论

+ Ronberg, Candes, Tao [^1], [^2], [^3]
+ 矩阵低秩近似

## 应用
下面代码在Julia 0.6.0环境下测试通过
### 测试矩阵

```julia
using PyPlot
using Convex
using SCS

# passing in verbose=0 to hide output from SCS
solver = SCSSolver(verbose = 0)
set_default_solver(solver);

# logistic function
lgc(x) = 1 ./ (1 + exp(-x));

# Construct a random m-by-n binary matrix matrix
m, n, k = 40, 40, 2
M = randn(m, k) * randn(k, n)       # Underlying low-rank matrix
fM = lgc(M)                     # Probability matrix, maps M onto interval [0,1]
Y = map(x -> x > rand() ? 1 : -1, fM) # True data, binary matrix

# Suppose that we only observe a fraction of entries in Y
n_obs = 800
Yobs = fill(NaN, (m, n))
obs = randperm(m * n)[1: n_obs]
Yobs[obs] = Y[obs]

# Plot the ground-truth, full dataset and our partial observations
figure(figsize = (7, 14))
subplot(1, 2, 1)
imshow(Y, cmap = ColorMap("bwr"), interpolation = "None")
xticks([]), yticks([]), title("True Data", fontweight = "bold")

subplot(1, 2, 2)
imshow(Yobs, cmap = ColorMap("bwr"), interpolation = "None")
xticks([]), yticks([]), title("Observed Data", fontweight = "bold")
show()
```

### Netflix

[^1]: Candes, Emmanuel J., and T. Tao. The Power of Convex Relaxation: Near-Optimal Matrix Completion. IEEE Transactions on Information Theory 56.5(2009):2053-2080.
[^2]: Starck, Jean Luc, E. J. Candes, and D. L. Donoho. The curvelet transform for image denoising. IEEE Press, 2002.
[^3]: Candes, Emmanuel J., and Y. Plan. Matrix Completion With Noise. Proceedings of the IEEE 98.6(2009):925-936.