---
layout: post
title: "优化"
author: "李军"
categories: journal
tags: [convex, optimization]
image:
  feature: optimization.jpg
  teaser: optimization-teaser.jpg
  credit: 
  creditlink: ""
---

本文简单讲解优化问题中的一些基本知识和技巧

#### 什么是优化

#### 凸优化

$$z = x^2 + y^2$$

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/optimize01.jpg)

Boyd

#### 非凸优化

+ Jacobian矩阵

+ Hessian矩阵

  ​

$$y = x^3$$

$$z = 2xy$$

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/optimize08.jpg)

$$z = x^2 - y^2$$

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/optimize02.jpg)

Rosenbrock函数

$$z = 100 (y - x^2)^2 + (1 - x)^2$$

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/rosenbrock.jpg)

$$F = 7 + 2(x+y)^2 - ysiny - x^3$$

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/optimize07.jpg)

$$f = 2x^2 + 4xy + y^2$$

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/optimize06.jpg)

函数F和f来自于Gil Strang, "Linear Algebra and Its Applications"，对应函数具有一般形式

$$f(x,y) = ax^2 + 2bxy + cy^2$$

a,b,c之间存在特殊关系

$$z = x^4 - 2 x^2 + y^2$$

```matlab
[X, Y] = meshgrid(-2:0.2:2,-2:0.2:2)
Z = X.^4 -2 * X.^2 + Y.^2
figure
surface(X, Y, Z)
view(3)
```

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/optimize03.jpg)

$$z = x^4 - y^4$$

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/optimize04.jpg)

monkey saddle

$$z = Re(x+iy)$$

that is,

$$z(x, y) = x^3 -3xy^2$$

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/optimize05.jpg)

鞍点问题

#### 机器学习中的应用
