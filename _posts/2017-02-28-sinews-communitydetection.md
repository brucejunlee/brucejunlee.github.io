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

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-community-1.jpg)

Dane Taylor outlines the advantages of layer aggregation in community detection, as well as best practices. Photo credit: Karthika Swamy Cohen.

Multilayer networks are data structures that can simultaneously capture several types of relationships between a set of nodes in a network. In such networks, each layer depicts a relational definition and provides its own set of information. Community structure across layers can then be consolidated to identify and quantify underlying relational patterns between nodes.

Real-world networks, such as social networks, are naturally represented by layers depicting different kinds of connections. Dane Taylor of University of North Carolina, Chapel Hill, uses this concept to study community structure in multilayer networks, such as, memory formation in brain networks, community detection in bioinformatics applications, and microbial interaction networks. 

At a minisymposium on Modeling and Computational Methods in Network Science and Applications at the SIAM Conference on Computational Science and Engineering being held in Atlanta, GA this week, Taylor outlined best practices and basic limitations in community detection. 

Basically, community detection or “clustering” involves clustering nodes in a community. This is followed by clustering layers. In a simple case, in a two-layer network, the two layers can represent complementary data sources and interconnected systems. To extend community detection to multilayer networks, Taylor's team uses the stochastic block model (SBM), which is widely used for community detection or clustering. SBM tends to produce graphs depicting communities that are subsets characterized by connectedness. The connectedness is described by edge densities; edges within communities may be more common than edges between communities. The SBM is important in statistics, machine learning, and network science.

In order to extract information from a multilayer network, sets of layers with meaningful similarities in community structure are identified and compiled. In the "strata multilayer stochastic block model'' (sMLSBM)—a probabilistic model for multilayer community structure—groups of layers called "strata'' are defined such that all layers within a stratum have community structure described by a common stochastic block model (SBM).

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-community-2.jpg)

Visualizing an empirical network of political blogs in parabolic representation shows two communities. Image credit: Dane Taylor, CSE17 presentation.

One example of this is clustering together microbial interaction networks that have similar community structure via a clustering of network layers. In order to find networks in microbiomes, networks are clustered based on whether or not they have similar community structure.

Taylor also described the effect of layer aggregation on community detectability. Layer aggregation saves memory and computation and is central to temporal network analysis, that is, networks that are time-dependent. Layer aggregation helps improve statistical inference and enhance community detection.

There are two approaches for layer aggregation: summing the layers’ adjacency matrices and thresholding the summation. Summing the layers' adjacency matrices causes the detectability limit to vanish with increasing numbers of layers.

Layer aggregation can thus affect and improve our ability to find community structure. 