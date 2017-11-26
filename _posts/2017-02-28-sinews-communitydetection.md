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

社区发现是网络科学和数据科学中的一个基本问题。社区发现的基本概念是任何数据集都可以表示成一个相互作用项的网络，这种网络的一个重要方面就是要理解哪些项是“相似的”从而形成社区。回答这个问题对很多领域都有裨益，如蛋白质交互、社会行为、推荐和系统等。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-community-1.jpg)

Dane Taylor outlines the advantages of layer aggregation in community detection, as well as best practices. Photo credit: Karthika Swamy Cohen.

Multilayer networks are data structures that can simultaneously capture several types of relationships between a set of nodes in a network. In such networks, each layer depicts a relational definition and provides its own set of information. Community structure across layers can then be consolidated to identify and quantify underlying relational patterns between nodes.

多层网络是可以同时捕获网络中一组节点间数种类型的关系的数据结构。在这样的网络中，每一层描述一个关系定义并提供它自身的一组信息。然后跨层社区结构可以被合并以识别和量化节点间的基本关系模式。

Real-world networks, such as social networks, are naturally represented by layers depicting different kinds of connections. Dane Taylor of University of North Carolina, Chapel Hill, uses this concept to study community structure in multilayer networks, such as, memory formation in brain networks, community detection in bioinformatics applications, and microbial interaction networks. 

社交网络等真实世界网络，很自然地由描述不同种类连接的层来表示。University of North Carolina, Chapel Hill的Dane Taylor利用这一概念研究多层网络中的社区结构，如大脑网络中的记忆形成、生物信息学中的社区发现和微生物交互网络等。

At a minisymposium on Modeling and Computational Methods in Network Science and Applications at the SIAM Conference on Computational Science and Engineering being held in Atlanta, GA this week, Taylor outlined best practices and basic limitations in community detection. 

本周在Atlanta, GA举办的SIAM Computational Science and Engineering会议上，有一个关于网络科学应用中建模和计算方法的微型研讨会，Taylor在会上概述了社区发现的最佳实践和基本局限。

Basically, community detection or “clustering” involves clustering nodes in a community. This is followed by clustering layers. In a simple case, in a two-layer network, the two layers can represent complementary data sources and interconnected systems. To extend community detection to multilayer networks, Taylor's team uses the stochastic block model (SBM), which is widely used for community detection or clustering. SBM tends to produce graphs depicting communities that are subsets characterized by connectedness. The connectedness is described by edge densities; edges within communities may be more common than edges between communities. The SBM is important in statistics, machine learning, and network science.

基本上，社区发现或“聚类”涉及社区中的节点集聚。接下来是层的集聚。在一个简单的两层网络中，这两层可以表示互补的数据源和互连的系统。为了将社区发现扩展到多层网络，Taylor团队使用了随机块模型（stochastic block model，SBM），它被广泛用于社区发现和聚类。SBM倾向于产生描绘以连通性为特征的社区子集的图。连通性用边密度来描述；社区内的边比社区间的边更常见。SBM在统计、机器学习和网络科学中非常重要。

In order to extract information from a multilayer network, sets of layers with meaningful similarities in community structure are identified and compiled. In the "strata multilayer stochastic block model'' (sMLSBM)—a probabilistic model for multilayer community structure—groups of layers called "strata'' are defined such that all layers within a stratum have community structure described by a common stochastic block model (SBM).

为了从多层网络中提取信息，我们在社区结构中确定并编制了具有相似性的层集。在“阶层式多层随机块模型”（strata multilayer stochastic block model，sMLSBM）-一种多层社区结构的概率模型-中，我们定义了“阶层”这样一种多层群落结构，使得在一个阶层内的所有层都具有一个由相同随机块模型（SBM）描述的社区结构。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-community-2.jpg)

Visualizing an empirical network of political blogs in parabolic representation shows two communities. Image credit: Dane Taylor, CSE17 presentation.

One example of this is clustering together microbial interaction networks that have similar community structure via a clustering of network layers. In order to find networks in microbiomes, networks are clustered based on whether or not they have similar community structure.

其中一个例子是通过网络层聚类将具有相似社区结构的微生物交互网络聚集在一起。为了发现微生物网络结构，我们根据它们是否有类似的社区结构将网络进行聚类。

Taylor also described the effect of layer aggregation on community detectability. Layer aggregation saves memory and computation and is central to temporal network analysis, that is, networks that are time-dependent. Layer aggregation helps improve statistical inference and enhance community detection.

Taylor还描述了层聚集对社区发现的影响。层聚集节省了内存和计算量，它是时间网络（也就是依赖于时间的网络）分析的核心。层聚集有助于提高统计推断和增强社区发现。

There are two approaches for layer aggregation: summing the layers’ adjacency matrices and thresholding the summation. Summing the layers' adjacency matrices causes the detectability limit to vanish with increasing numbers of layers.

层聚集有两步：层间的邻接矩阵求和以及对求和结果进行阈值处理。层间邻接矩阵的求和会引起社区发现的局限性，这一局限会随着层数的增加而消失。

Layer aggregation can thus affect and improve our ability to find community structure. 

因此，层聚集可以影响和提高我们发现社区结构的能力。