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

[Google TensorFlow](www.tensorflow.org)是表示机器学习算法的接口，并且是执行这些算法的实现平台。使用TensorFlow表示的计算可以在多种多样的系统中几乎无修改地执行。这些系统包括从手机、平板电脑等移动设备到数以百计的机器和数以千计的GPU等计算设备组成的大规模分布式系统。这样的系统非常灵活，可以被用来表示大量算法，包括深度神经网络模型的训练和推理。它也被运用到研究中，以及将机器学习系统部署到横跨数十个计算机科学和其它领域的生产中，包括语音识别，计算机视觉，机器人学，信息检索，自然语言处理，地理信息抽取和计算药物发现等。



#### 引言 

Google Brain在2011年开始了一个探究将大规模深度神经网络用于研究和Google产品中的项目。DistBelief作为Google第一代可扩展分布式训练推理系统，在项目早期被构建，并很好地被用于无监督学习、语言表示、图像分类、目标检测、视频分类、语音识别、序列预测、围棋落子、行人检测、增强学习和其它很多领域。当然，DistBelief还被用于Google其它产品中，包括Google搜索、广告系统、Google照片、Google地图、街景、Google翻译、YouTube等。

基于前面开发DistBelief的经验和对深度神经网络的更全面理解，Google Brain开发了第二代大规模机器学习系统TensorFlow。TensorFlow的计算使用类dataflow模型来描述，并将它们映射在多种不同的硬件平台上，包括在Android、iOS等移动设备上运行推理到包含一个或多个GPU的单机上使用的中等规模系统再到运行在包含数以千计的GPU的数百台机器上的大规模训练系统。拥有这样一个横跨如此多平台的独立系统大大简化了机器学习在现实中的使用。TensorFlow计算被表示成带状态的数据流图，并且只关注在研究中快速进行新模型试验和在生产中的高性能和健壮性方面的灵活性。当然，TensorFlow还允许通过核心模型数据流图的副本和并行执行来表达多种并行机制。



