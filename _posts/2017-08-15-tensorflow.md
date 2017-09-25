---
layout: post
title: "TensorFlow"
author: "李军"
categories: journal
tags: [tensorflow, deep learning]
image:
  feature: tf.jpg
  teaser: tf-teaser.jpg
  credit: 
  creditlink: ""
---

Google [TensorFlow](www.tensorflow.org)是表示机器学习算法的接口，并且是执行这些算法的实现平台。使用TensorFlow表示的计算可以在多种多样的系统中几乎无修改地执行。这些系统包括从手机、平板电脑等移动设备到数以百计的机器和数以千计的**GPU**等计算设备组成的大规模分布式系统。这样的系统非常灵活，可以被用来表示大量算法，包括深度神经网络模型的训练和推理。它也被运用到研究中，以及将机器学习系统部署到横跨数十个计算机科学和其它领域的生产中，包括语音识别，计算机视觉，机器人学，信息检索，自然语言处理，地理信息抽取和计算药物发现等。



## 引言 

**Google Brain**在2011年开始了一个探究将大规模深度神经网络用于研究和Google产品中的项目。DistBelief作为Google第一代可扩展分布式训练推理系统，在项目早期被构建，并很好地被用于无监督学习、语言表示、图像分类、目标检测、视频分类、语音识别、序列预测、围棋落子、行人检测、增强学习和其它很多领域。当然，DistBelief还被用于Google其它产品中，包括Google搜索、广告系统、Google照片、Google地图、街景、Google翻译、YouTube等。

基于前面开发DistBelief的经验和对深度神经网络的更全面理解，Google Brain开发了第二代大规模机器学习系统TensorFlow[^1]。TensorFlow的计算使用类dataflow模型来描述，并将它们映射在多种不同的硬件平台上，包括在Android、iOS等移动设备上运行推理到包含一个或多个GPU的单机上使用的中等规模系统再到运行在包含数以千计的GPU的数百台机器上的大规模训练系统。拥有这样一个横跨如此多平台的独立系统大大简化了机器学习在现实中的使用。TensorFlow计算被表示成带状态的数据流图，并且只关注在研究中快速进行新模型试验和在生产中的高性能和健壮性方面的灵活性。当然，TensorFlow还允许通过核心模型数据流图的副本和并行执行来表达多种并行机制。

## 基本概念
一个TensorFlow计算是由节点(**Node**)集组成的有向图来描述的。这个图表示一个数据流计算，扩展来允许某些节点维护和更新反复出现的状态(state)，并带有分支循环结构。客户端(**Client**)通常使用前端语言(如C++、Python)来构造一个计算图。

```python
import tensorflow as tf
b = tf.Variable(tf.zeros([100]))
W = tf.Variable(tf.random_uniform([784, 100], -1, 1))
x = tf.placeholder(name = "x")
relu = tf.nn.relu(tf.matmul(W, x) + b)
cost = [...]

sess = tf.Session()
for step in xrange(0, 10):
	input = ...construct 100-D input array...
	result = sess.run(cost, feed_dict = {x: input})
	print step, result
```

在TensorFlow图中，每个节点表示一个操作(**Operation**)实例，有零或多个输入，有零或多个输出。沿着通常的边流(从输出到输入)的值称为张量(**Tensor**)。还有一类特殊边也出现在图中，称为控制依赖(**control dependencies**)，在这类边上没有数据流，它们表示在控制依赖的目标节点开始执行之前控制依赖的源节点必须完成执行。

#### 操作
一个操作有一个名称(*name*)，并表示一个抽象计算(如矩阵乘法、加法)。一个操作也有属性(*attribute*)。属性的一个常见用处是在不同张量元素类型上的多态(polymorphic)操作(如两个float类型张量加法和两个int32类型张量加法)。核(*kernel*)是可以运行在一类特殊设备(如CPU、GPU)上的操作实现。

类别  | 样例
------------- | -------------
按元操作  | Add, Sub, Mul, Div, Exp, Log, Greater, Less, Equal
数组  | Concat, Slice, Split, Constant, Rank, Shape, Shuffle
矩阵  | MatMul, MatrixInverse, MatrixDeterminant
状态(stateful)  | Variable, Assign, AssignAdd
神经网络  | SoftMax, Sigmoid, ReLU, Convolution2D, MaxPool
断点(checkpoint) | Save, Restore
队列，同步  | Enqueue, Dequeue, MutexAcquire, MutexRelease
控制流  |Merge, Switch, Enter, Leave, NextIteration


#### 会话
客户端程序通过一个会话(**Session**)可以与TensorFlow系统进行交互。会话接口支持**Extend**方法利用额外的节点和边来增强当前由会话管理的图。其它由会话支持的主要操作是**Run**。使用**Run**的参数，TensorFlow可以计算所有节点的传递闭包(*transitive closure*)

#### 变量
变量(**Variable**)是一类特殊的操作，它可以返回一个在图的执行中持续存在的可变张量的句柄(*handle*)。这些句柄可以传递给特殊操作，如*Assign*和*AssignAdd*。

## 实现

#### 设备

#### 张量

## 扩展

## 优化

## 经验

## 工具

## 应用

#### 图片标题

#### 运动检测




## 文献
[^1]: Jeff Dean et al., TensorFlow: Large-Scale Machine Learning on Heterogeneous Distributed Systems.