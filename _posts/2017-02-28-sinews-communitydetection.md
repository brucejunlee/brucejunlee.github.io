---
layout: post
title: "[SIAM NEWS] Community Detection in Network Science"
author: "李军"
categories: journal
tags: [siam, community]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

By <u>Karthika Swamy Cohen</u>

February 28, 2017

[Karthika Swamy Cohen is the managing editor of SIAM News.]

Community detection is a fundamental problem in network and data science. The basic concept of community detection is that any data set can be represented as a network of interacting items, and an important aspect of such networks is to understand which items are “alike” and thus form communities. Answering this question is helpful in a wide variety of areas, such as, protein interactions, social behavior, recommendation, systems, etc.

社区发现是网络和数据科学中的一个基本问题。社区检测的基本概念是，任何数据集都可以表示为一个相互作用的项目网络，而这种网络的一个重要方面是理解哪些项目是“相似的”，从而形成社区。回答这个问题有助于广泛的领域，如蛋白质相互作用，社会行为，推荐，系统等。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-community-1.jpg)

Dane Taylor outlines the advantages of layer aggregation in community detection, as well as best practices. Photo credit: Karthika Swamy Cohen.

Multilayer networks are data structures that can simultaneously capture several types of relationships between a set of nodes in a network. In such networks, each layer depicts a relational definition and provides its own set of information. Community structure across layers can then be consolidated to identify and quantify underlying relational patterns between nodes.

多层网络是数据结构，可以同时捕获网络中一组节点之间的几种类型的关系。在这样的网络中，每一层描述一个关系定义并提供它自己的一组信息。然后跨层的社区结构可以被合并，以识别和量化节点之间的底层关系模式。

Real-world networks, such as social networks, are naturally represented by layers depicting different kinds of connections. Dane Taylor of University of North Carolina, Chapel Hill, uses this concept to study community structure in multilayer networks, such as, memory formation in brain networks, community detection in bioinformatics applications, and microbial interaction networks. 

真实世界的网络，如社交网络，自然是由不同的连接层描述的。查珀尔希尔北卡罗来那大学的Dane Taylor利用这一概念研究多层网络中的社区结构，如脑网络中的记忆形成、生物信息学中的社区检测和微生物相互作用网络。

At a minisymposium on Modeling and Computational Methods in Network Science and Applications at the SIAM Conference on Computational Science and Engineering being held in Atlanta, GA this week, Taylor outlined best practices and basic limitations in community detection. 

在minisymposium在网络科学和计算建模方法研究与应用在科学和工程计算的在亚特兰大举行的暹罗会议上，GA的这一周，泰勒提出的最佳实践和基本局限在社区检测。

Basically, community detection or “clustering” involves clustering nodes in a community. This is followed by clustering layers. In a simple case, in a two-layer network, the two layers can represent complementary data sources and interconnected systems. To extend community detection to multilayer networks, Taylor's team uses the stochastic block model (SBM), which is widely used for community detection or clustering. SBM tends to produce graphs depicting communities that are subsets characterized by connectedness. The connectedness is described by edge densities; edges within communities may be more common than edges between communities. The SBM is important in statistics, machine learning, and network science.

基本上，社区检测或“集群”涉及社区中的节点群集。接下来是集群层。在一个简单的情况下，在两层网络中，这两层可以表示互补的数据源和相互连接的系统。扩大社区检测多层网络，泰勒的团队使用的随机块模型（SBM），它被广泛用于社区检测和聚类。我倾向于产生图描绘社区的特点是连通子集。连通性用边缘密度来描述；社区内的边缘可能比社区之间的边缘更为普遍。豆粕是重要的统计，机器学习和网络科学。

In order to extract information from a multilayer network, sets of layers with meaningful similarities in community structure are identified and compiled. In the "strata multilayer stochastic block model'' (sMLSBM)—a probabilistic model for multilayer community structure—groups of layers called "strata'' are defined such that all layers within a stratum have community structure described by a common stochastic block model (SBM).

为了从多层网络中提取信息，确定并编译了具有社区结构相似性的层集。在“地层多层随机块模型”（smlsbm）-一种概率模型的多层群落结构层组称为“阶层”的定义，在一层的所有层群落结构的一个共同的随机块模型（SBM）。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-community-2.jpg)

Visualizing an empirical network of political blogs in parabolic representation shows two communities. Image credit: Dane Taylor, CSE17 presentation.

One example of this is clustering together microbial interaction networks that have similar community structure via a clustering of network layers. In order to find networks in microbiomes, networks are clustered based on whether or not they have similar community structure.

其中一个例子是通过网络层的聚类将具有相似社区结构的微生物相互作用网络聚集在一起。为了在微生物发现网络，网络集群根据他们是否有类似的群落结构。

Taylor also described the effect of layer aggregation on community detectability. Layer aggregation saves memory and computation and is central to temporal network analysis, that is, networks that are time-dependent. Layer aggregation helps improve statistical inference and enhance community detection.

泰勒还描述了层聚集对社区可探测性的影响。层聚合节省了内存和计算量，是时间网络分析的核心，也就是时间依赖网络。层聚合有助于提高统计推断和增强社区检测。

There are two approaches for layer aggregation: summing the layers’ adjacency matrices and thresholding the summation. Summing the layers' adjacency matrices causes the detectability limit to vanish with increasing numbers of layers.

层聚合有两种方法：求层邻接矩阵和求和求和。求出层的邻接矩阵使探测极限随着层数的增加而消失。

Layer aggregation can thus affect and improve our ability to find community structure. 

因此，层聚合可以影响和提高我们发现社区结构的能力。