---
layout: post
title: "随机矩阵理论(一): 综述"
author: "李军"
categories: journal
tags: [RMT]
image:
  feature: 
  teaser: 
  credit: 
  creditlink: ""
---

随机矩阵理论自一开始就注重理论联系实际，随着时间发展已经深入到很多学科领域，如随机过程，PDE，统计，图论，医药，金融，信号处理，无线通信，甚至机器学习，深度学习等计算机科学中。因此，我们很难毫无疏漏地把RMT讲述清楚。下面，我将RMT分成几个不同部分书写，不定期地推出。本文是随机矩阵理论系列的第一篇文章，主要描述一些产生背景，发展过程和几个重要的定理定律及其证明方法。

#### 什么是随机矩阵



#### 预备知识

+ 矩阵论
+ 微积分
+ 概率论

#### 历史
+ 史前：Fisher，PL Hsu，Wishart，LK Hua
+ 创世[1950s]：E. Wigner
+ 第一阶段[1960s-1980s]：Dyson，Marcenko-Pastur，M Mehta
+ 第二阶段[1990s]：Nick Trefethen，Alan Edelman，Tracy-Widom，Zhidong Bai，Silverstein，Peter Forrester
+ 第三阶段[2000s-]：Terence Tao，Donoho，Percy Deift，Tropp，HorngTzer Yau，Vu，Raj Rao Nadakuditi，Dimitris Achlioptas，Couillet，Robert Qiu，Sheehan Olver，Thomas Trogdon，Pennington

#### 定理

+ Wigner半圆定律
+ Girko圆律
+ 1/4圆律
+ Marcenko-Pastur定律
+ Tracy-Widom定律

#### 其它性质

+ Edelman的奇异值分布
+ 特征值最近邻分布
+ free probability theory

#### Types
+ Gaussian ensemble
+ Laguerre ensemble
+ Circular ensemble

#### softwares
+ [Mathematica](https://www.wolfram.com/language/11/random-matrices/?product=mathematica)
+ Python: see github.com
+ Julia: RandomMatrices.jl

#### 应用

* 数学：Riemann zeta function，正交多项式，HorngTzer Yau，Terry Tao，Alan Edelman，Peter Forrester
* 组合学：longest increasing subsequence
* 物理：原子核能级，固体行为，晶体学，totally asymmetric simple exclusion process，spin glass，量子物理，<u>量子混沌</u>，QCD，多体系统
* 数学物理：可积系统，Percy Deift，Tracy，Widom
* 信号处理：random matrix-based signal detection[Raj Rao Nadakuditi]，wireless communication[Tulino & Verdu]，Roman Couillet[Random matrix methods in wireless communications]，Robert C. Qiu's works on smart grid，compressed sensing[Donoho, Candes，Tao]
* 统计：random matrices in high-dimensional data analysis，Zhidong Bai，Jinho Baik，Silverstein
* 金融统计：Wishart matrix，cross correlation in financial data
* 图论：Erdos-Renyi图
* 机器学习：<u>determinantal point process</u>，random matrices in data analysis[Dimitris Achlioptas]，matrix approximation，random matrices meet machine learning，<u>Joel A Tropp</u>[An introduction to Matrix concentration inequalities]，Numerical Linear Algebra[Golub，Drineas，Mahoney，Gil Strang]
* 深度学习：Echo state machine，Extreme learning machine，</u>Roman Couillet</u>，<u>Jeffrey pennington</u>
* 复杂网络：<u>community detection in social network</u>，bus/subway arrival and departure analysis in a city，<u>Thomas Trogdon</u>


