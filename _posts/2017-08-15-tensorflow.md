---
layout: post
title: "TensorFlow(一)：初识"
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

基于前面开发DistBelief的经验和对深度神经网络的更全面理解，Google Brain开发了第二代大规模机器学习系统TensorFlow[^1]。TensorFlow的计算使用类dataflow模型来描述，并将它们映射在多种不同的硬件平台上，包括在Android、iOS等移动设备上运行推理到包含一或多个GPU的单机上使用的中等规模系统再到运行在包含数以千计的GPU的数百台机器上的大规模训练系统。拥有这样一个横跨如此多平台的独立系统大大简化了机器学习在现实中的使用。TensorFlow计算被表示成带状态的数据流图，并且只关注在研究中快速进行新模型试验和在生产中的高性能和健壮性方面的灵活性。当然，TensorFlow还允许通过核心模型数据流图的副本和并行执行来表达多种并行机制。

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

### 操作
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

### 会话
客户端程序通过一个会话(**Session**)可以与TensorFlow系统进行交互。会话接口支持**Extend**方法利用额外的节点和边来增强当前由会话管理的图。其它由会话支持的主要操作是**Run**。使用**Run**的参数，TensorFlow可以计算所有节点的传递闭包(*transitive closure*)

### 变量
变量(**Variable**)是一类特殊的操作，它可以返回一个在图的执行中持续存在的可变张量的句柄(*handle*)。这些句柄可以传递给特殊操作，如*Assign*和*AssignAdd*。

## 实现
客户端程序是TensorFlow系统的主要部分，它使用会话接口与主进程(master)和工作进程(worker process)保持通信，其中每个工作进程负责一或多个计算设备(CPU、GPU)的访问，以及在这些设备(*devices*)上图节点的执行。TensorFlow分为本地(local)实现和分布式(distributed)实现两种方式。当客户端程序，主进程和工作进程都运行在单机上时，采用本地实现；当客户端程序，主进程和工作进程运行在不同机器的不同进程中时，采用分布式实现。在分布式环境下，这些不同任务(*task*)是由集群调度系统(*cluster scheduling system*)管理的作业容器(*containers in jobs*)。

### 设备
设备是TensorFlow的计算中心。每个工作进程负责一或多个设备，每个设备有一个设备类型和一个名称。设备名由识别设备类型的部分，工作进程内设备索引(*index*)组成；在分布式环境下还包括作业识别和工作进程的任务(当设备是本地(*local to process*)时，用本地主机(*localhost*)代替工作进程)。TensorFlow通过注册机制(**registration mechanism**)提供了对于除CPU、GPU外的新设备实现。每台设备负责设备内存的分配、释放，安排更高层级请求的核的执行。

设备类别  | 样例
------------- | -------------
CPU  | /job:localhost/device:cpu:0
GPU  | /job:worker/task:17/device:gpu:3

### 单设备执行
单设备单工作进程是最简单的执行场景。图中节点的执行顺序对应节点间的依赖关系。

### 多设备执行
TensorFlow主要负责将图计算映射到多台可行设备上。

#### 节点放置(placement)机制
节点放置算法的一个输入是成本(*cost*)模型，该模型包含每个节点的输入张量和输出张量的大小估计，以及每个节点所需的计算时间估计。

放置算法从计算图的源节点开始，随着时间发展模拟系统中每台设备的活动。对于有多台可行(*feasible*，如果设备没有提供实现特殊操作的核的话，那么这台设备也许就不是可行的)设备的节点来说，放置算法采用贪心启发式方法，将节点放置在每台可行设备上，来检查节点完成时间的效果。

#### 跨平台通信
计算完节点放置算法后，计算图被划分成一系列子图，每台设备上放置一个子图。同时，任何从节点`x`(假设在设备**A**中)跨设备到节点`y`(假设在设备**B**中)的边将被移除，由从`x`到设备**A**中一个新的`Send`节点的边和相应的设备**B**中`Receive`节点到`y`节点的边来代替。

当我们插入`Send`节点和`Receive`节点时，我们对特殊设备上特殊张量的所有用户进行规范化，使得它们只使用一个`Receive`节点。

### 分布式执行
图的分布式执行与多设备执行非常相似。在放置完设备后，每台设备上创建一个子图。横跨工作进程通信的`Send`/`Receive`节点对使用TCP、RDMA等远程通信机制跨机器边界来迁移数据。

#### 容灾(failure tolerance)
很多地方都可以检测到分布式执行中的故障(*failure*)。主要包括(a)`Send`和`Receive`节点对之间的通信错误(*error*) (b)从主进程到工作进程的周期检测(*health-check*)。当检测到故障时，整个图执行将被终止，并从头重新开始。

## 扩展
### 梯度计算
TensorFlow内置支持自动梯度计算。
```python
[db, dW, dx] = tf.gradients(C, [b, W, x])
```

### 部分执行
图中每个节点都有一个名称，节点的每个输出都由源节点和该节点的输出端口(编号从0开始)来识别，如"bar:0"指的是`bar`节点的第一个输出，而"bar:1"指的是第二个输出。

`Run`调用的两个参数有助于执行的计算图的精确子图计算。首先，`Run`接受从形如name:port的名称到提供的张量值可选映射的输入。其次，`Run`接受输出名，它是形如name[:port]用于说明节点执行的输出列表。

图基于输入输出值进行变换。在输入中的每个node:port被一个`feed`节点替换。每个带端口的输出名链接一个特殊的`fetch`节点。

### 控制流
尽管没有显式控制流的数据流图具有丰富的表达能力，但是支持条件(*conditional*)和循环(*loop*)的数据流图可以导致更加精确和高效的机器学习算法表示。

TensorFlow引入了一小部分主要的控制流操作，使得TensorFlow能够处理循环(*cyclic*)数据流图。`Switch`和`Merge`操作使我们能够基于布尔张量的值跳过整个子图的执行。`Enter`、`Leave`和`NextIteration`操作使我们能够表示迭代。

TensorFlow运行时实现标签(*tags*)和帧(*frames*)的概念。循环的每个迭代由标签唯一确定，执行状态由帧表示。多个迭代可以并发执行。

### 队列
队列(**Queue**)允许计算图的不同部分异步执行，使用`Enqueue`和`Dequeue`操作来处理数据。`Enqueue`操作阻塞直到队列中有可用空间。`Dequeue`操作阻塞直到队列中有最小可用元素。

除了通常的**FIFO**队列外，TensorFlow还实现了**shuffle**队列，该队列将大的内存缓冲区(*in-memory buffer*)中的元素随机洗牌。

### 容器
容器用于管理长期存在的可变状态。

## 优化
### 数据通信和内存使用
+ as-soon-as-possible(**ASAP**) calculation
+ as-late-as-possible(**ALAP**) calculation

### 优化库
#### 矩阵乘法
+ BLAS
+ cuBLAS

#### GPU库
+ cuda-convnet
+ cuDNN

#### 开源Eigen线性代数库扩展

## 经验
+ 构建工具来观察给定模型参数的精确个数
+ 从小网络开始，在扩展到更大网络中
+ 保证停止学习时机器学习系统间目标(损失函数)相匹配：将学习率设为0有助于观察模型参数随机初始化造成的异常行为
+ 在调试分布式实现前先通过单机实现：能够识别由于竞争条件(*race condition*)和非原子(*non-atomic*)操作造成的错误(*bug*)
+ 防止数值误差：数值库在处理非有限浮点数方面是不一致的
+ 分析网络块来理解数值误差的大小

## 工具
### TensorBoard：计算图结构和统计信息可视化

### 性能追踪：Google内部工具EEG
+ Linux核ftrace
+ CUDA概要工具接口(CUDA Profiling Tools Interface, CUPTI)

## 系统比较
下面并没有针对Caffe2，MXNet，PyTorch和**PaddlePaddle**等最新发布的框架进行比较分析

+ 不同于分布式TensorFlow实现，Theano，Torch，Caffe，Chainer，CNTK(Computational Network Toolkit)这些系统将计算映射到单机上
+ 像Theano和Chainer一样，TensorFlow支持符号微分
+ 像Caffe一样，TensorFlow由一个C++编写的内核，这大大简化了不同生产环境中模型的部署，包括内存受限计算能力受限的环境，如移动设备等
+ 同DistBelief和Project Adam一样，TensorFlow允许计算横跨多个机器多台计算设备
+ **Spark**，通过“弹性分布式数据集(resilient distributed datasets, RDD)”，来优化用于重复访问相同数据的计算

## 文献
[^1]: Jeff Dean et al., TensorFlow: Large-Scale Machine Learning on Heterogeneous Distributed Systems.