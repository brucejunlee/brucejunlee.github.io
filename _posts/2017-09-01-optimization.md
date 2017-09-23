---
layout: post
title: "优化"
author: "李军"
categories: journal
tags: [convex, optimization]
image:
  feature: 
  teaser: 
  credit: 
  creditlink: ""
---

本文简单讲解优化问题中的一些基本知识和技巧

#### 什么是优化

#### 凸优化

$$z = x^2 + y^2$$

Boyd

#### 非凸优化

+ Jacobian矩阵

+ Hessian矩阵

  ​

$$y = x^3$$

$$z = x^2 - y^2$$

$$z = x^4 - 2 x^2 + y^2$$

```matlab
[X, Y] = meshgrid(-2:0.2:2,-2:0.2:2)
Z = X.^4 -2 * X.^2 + Y.^2
figure
surface(X, Y, Z)
view(3)
```



$$z = x^4 - y^4$$

monkey saddle

鞍点问题

#### 机器学习中的应用
