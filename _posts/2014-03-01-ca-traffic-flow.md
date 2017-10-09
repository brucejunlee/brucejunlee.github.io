---
layout: post
title: "元胞自动机(二)：交通流"
author: "李军"
categories: journal
tags: [cellular automata, traffic flow, mathematics]
image:
  feature: trafficflow.jpg
  teaser: trafficflow-teaser.jpg
  credit: 
  creditlink: ""
---

### 交通流

#### 概述

#### 理论

三相交通理论

#### 相变现象

#### 几类规则

rule0-rule255

#### 模型仿真

Monte-Carlo方法不仅可以用于计算，还可以用于模拟系统内部的随机运动。下面的示例根据Nagel-Schreckenberg(NS)模型来模拟单车道的交通拥堵，NS模型中的车辆运动满足如下规则：

```nothing
+ 当前速度为v
+ 如果前面没车，它在下一秒的速度会提高到v+1，直到达到规定的最高限速
+ 如果前面有车，距离为d，且d<v，那么它在下一秒的速度会降低到d-1
+ 此外，司机还会以概率p随机减速，将下一秒的速度降低到v-1
```

下面，在一条直线上，随机产生100个点，代表道路上的100辆车，另取概率p为0.3。通过模拟形成时空图，横轴表示空间距离(从左往右)，纵轴表示时间(从上往下)，该模型会随机产生交通拥堵。从而证明，单车道即使没有任何原因，也会产生交通拥堵，这就是拥堵的内在自发性。