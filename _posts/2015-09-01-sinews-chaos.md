---
layout: post
title: "[SIAM NEWS] Chaos and its Manifestations"
author: "李军"
categories: journal
tags: [siam, chaos]
image:
  feature: 
  teaser: 
  credit: 
  creditlink: ""
---

By Evelyn Sander and <u>James A. Yorke</u>

September 01, 2015

[Evelyn Sander is a professor of mathematics at George Mason University. Jim Yorke is a Distinguished University Research Professor of Mathematics and Physics at the University of Maryland, College Park.]

Typical dynamical systems can either have simple trajectories, such as steady states or periodic or quasiperiodic orbits, or they can be chaotic. While simple behavior is well understood, chaos is defined in so many different ways that is it confusing and difficult to get a reasonable answer to the simple question: what is the definition of chaos? We assert that this is the wrong question to ask.

典型的动力系统要么有简单的轨迹，如稳定状态、周期或拟周期轨道，要么就是混沌的。简单行为很好理解，但混沌有许多不同方式的定义，这使得获得这一问题的一个合理的答案变得非常令人困惑和困难，即这样一个简单的问题：混沌的定义是什么？我们认为这本身就是一个错误的问题。

Chaos does not have a satisfactory single mathematical definition, not because it is not a single mathematical concept, but rather because it has many mathematical manifestations in many different situations. In this regard, we are reminded of the 2500-year-old parable of the blind monks and the elephant. Each monk touches a different part of the elephant; a monk feeling a tusk thinks the elephant is a spear, while others encounter different manifestations of the elephant—a rope-like tail, perhaps, or column-like legs. When we observe a chaotic system, we are blind to the enormity of the concept and observe only a limited number of aspects of the system’s chaotic nature.

混沌并没有一个令人满意的简单的数学定义，这并不是因为它本身不是一个简单的数学概念，而是因为它在许多不同的情况下有许多数学表现形式。在这方面，我们想起了2500年前盲人摸象的寓言故事。每个盲人都摸到了大象的不同部分；触到了獠牙的盲人认为大象是一个长矛，而其他盲人遇到了大象的不同表现形式，如绳状的尾巴或柱状的腿。当我们观察一个混沌系统时，我们也看不清这一概念的庞大棘手，只观察到系统混沌性质极其有限的方面。

In this article we discuss a variety of the manifestations and mathematical definitions of chaos. Our underlying message is that although it is possible to find pairs of definitions, one of which indicates that a system is chaotic and the other that it is not, this phenomenon is the exception, rather than the rule. We conjecture that, typically, the different forms of chaos are equivalent.

在这篇文章中，我们讨论了混沌的各种表现形式和数学定义。我们的基本信息是，虽然有可能找到一对定义，其中一个表明系统是混沌的，而另一个表明系统不是混沌的，但这种现象只是一种例外，不是规则。我们推测，通常情况下，混沌的不同表现形式是等价的。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-chaos-1.jpg)

Figure 1. A homoclinic tangle with the chaotic complexity described by Poincaré.

Arguably the earliest observation of mathematical chaos occurred in the context of Newtonian mechanics. Henri Poincaré wrote a proof of the stability of the solar system, a result for which he won a substantial prize from King Oscar II of Sweden in 1890. After the prize was awarded, Lars Edvard Phragmén pointed out a substantial omission: Poincaré had assumed that only simple behavior could occur in a situation in which, in fact, it is possible to have chaotic behavior and what is now known as a transverse homoclinic orbit. In particular, there is a Cantor set of points with the property that the trajectory through almost any one of them occasionally comes arbitrarily close to that steady state both forward and backward in time, but with large excursions along the way.

可以说，最早的数学混沌观测出现在牛顿力学的背景下。Henri Poincaré写了一个太阳系稳定性的证明，因此他在1890年赢得了瑞典国王奥斯卡二世颁发的一个重要奖项。在颁奖礼后，Lars Edvard Phragmén指出了一个重要的疏漏：Poincaré假设在这一情况下只有简单行为，但事实上，混沌行为也可能发生，现在它被称为横向同宿轨道。特别是，有一个康托点集，它具有这样的性质，即穿过其中几乎任何一个点的轨迹偶尔会随着时间往前往后都非常接近稳定状态，但它需要历经很长一段路经。

Poincaré's proof of the stability of the solar system completely collapsed, and the question remains open today (although the high likelihood of the survival of the planets in their orbits has been verified numerically to the expected time of the sun’s demise). Poincaré then undertook a major rewrite of the paper, in the course of which he discovered the underlying complexity of dynamical systems. In his words, “If one seeks to visualize the pattern formed . . . a chain-link network of infinitely fine mesh . . . one will be struck by the complexity. . ., which I am not even attempting to draw” [3]. Thankfully, the existence of computers makes it possible to depict this situation (shown in Figure 1).

Poincaré关于太阳系稳定性的证明完全坍塌了，这至今仍然是开放问题（虽然已经数值上验证了行星存活在它们的轨道上十有八九要直到太阳死亡了）。Poincaré对那篇论文进行了重大修改，在这一过程中，他发现了动力系统的基本复杂性。用他的话来说，“如果一个人试图可视化形成模式...无限细网格构成的链式网络...人们会受困于其复杂性...我甚至没法试图将它们画出来”[3]。幸运的是，计算机的存在使我们能够描述这种情况（如图1所示）。

Following this path of ideas, Stephen Smale showed in 1967 that even in a simple two-dimensional map known as a horseshoe map, one sees the same complexity as in transverse homoclinic orbits; in fact, horseshoe maps are embedded in any system containing a transverse homoclinic orbit. This aspect of chaos is useful when visualization is difficult but analysis is tractable, as for delay differential equations and partial differential equations. Chaos of this type can often be transient—that is, it cannot be observed through direct simulations of a trajectory or in physical experiments. Furthermore, the characterization is not quantitative.

沿着这条思路，Stephen Smale在1967年展示了，即使在如马蹄形映射这样简单的二维映射中，人们也能看到如在横向同宿轨道中相同的复杂性；事实上，马蹄形映射内嵌在任何含有横向同宿轨道的系统中。混沌的这一方面在可视化很难但分析易于处理时是很有用的，正如在时滞微分方程和偏微分方程中一样。这类混沌通常是瞬态的，即不能通过轨迹的直接模拟或物理实验直接观察。此外，特性也不能量化。

In the course of numerical experiments for models of two very different natural systems, Yoshisuke Ueda (in 1961) and Edward Lorenz (in 1963) observed a robust but highly irregular topology in the trajectories of the systems. This “fractal topology” is a hallmark of attracting chaotic systems known as strange attractors; their measurement has since been made more precise in the form of attractor-dimension calculations. A general definition of strange attractors is still lacking, however, except for the subtype of rank-one attractors. Transverse homoclinic orbits often play a key role in shaping the geometry of strange attractors, and these concepts have been rigorously shown to be tightly related in many subclasses of systems.

在两个非常不同的自然系统模型的数值实验过程中，Yoshisuke Ueda（上田晥亮，1961年）和Edward Lorenz（1963年）在系统轨迹上观察到一个健壮但高度不规则的拓扑结构。这种“分形拓扑”就是被称为奇异吸引子的吸引混沌系统的一个标志，自此以后它们的测量以吸引子维数计算的形式变得更加精确。然而，除了秩为1的吸引子亚型外，仍然缺少对奇异吸引子的一般定义。横向同宿轨道在刻画奇异吸引子的几何结构中经常起着关键作用，这些概念已经严格展示了与许多子系统的紧密关联。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-chaos-2.jpg)

Figure 2. Eight basins of attraction for the forced–damped pendulum. The geometric complexity of the basins results from the chaos on their boundaries.

Rather than providing full knowledge of a system, experiments often give rise to time-series data. In 1975, Jerry Gollub and Harry Swinney demonstrated that the time-series data from Taylor–Couette fluid flow experiments had the chaotic hallmark of a broad power spectrum. In fact, the closely related Lyapunov exponent is the current most commonly used metric for characterizing chaos; using added information about the behavior of nearby orbits, the Lyapunov exponent indicates the degree of stretching along solutions. For experimental high-dimensional chaos, it is not possible in general to observe this stretching. The concept of stretching also appears in the definition of scrambled sets of Li and Yorke. Aside from stretching, another way to measure chaos is the possession of positive entropy. If the number of “distinct” orbits of period n is proportional to a^n, then the entropy is proportional to log(a). As with chaos, there are a variety of types of entropy. Each of the above-mentioned concepts can be shown to be distinct, although they appear to overlap in all but rather extreme cases, as discussed in [2].

实验经常产生时间序列数据，并不能给出系统的全部知识。1975年，Jerry Gollub和Harry Swinney证明了来自Taylor–Couette流体流动实验的时间序列数据具有广泛能谱的混沌特征。事实上，密切相关的Lyapunov指数是目前最常用的表征混沌的指标；使用附加的关于附近轨道行为的信息，Lyapunov指数可以表示沿解的拉伸程度。对于实验中的高维混沌而言，一般观察不到这种拉伸。拉伸的概念也出现在Li和Yorke关于混沌集（scrambled sets）的定义中。除了拉伸外，测量混沌的另一种方法是拥有正熵。如果周期n的“不同”轨道数与a<sup>n</sup>成正比，则熵与对数log(a)成比例。与混沌一样，有各种各样类型的熵。上面提到的每一个概念可以被证明是不同的，尽管它们似乎在极端情况下有所重叠，如[2]中讨论的那样。

The importance of non-attracting chaos is often overlooked, as it cannot be seen either by direct simulation or experimental observation. This behavior, though not stable, can organize the underlying behavior of the system and can be robust under changes to the system parameters. Such is the case for chaotic saddles. Figure 2, for example, shows the basins of eight attractors for the forced–damped pendulum. The eight attractors are simply periodic and fixed points. The chaotic saddle on the boundary of the basins causes the geometric complexity. The progression of the basins as the forcing changes can be seen in our YouTube video [4]. 

人们常常忽略非吸引混沌的重要性，因为它不能通过直接模拟或实验观察看到。这种行为虽然不稳定，但是它可以组织系统的基本行为，并且在系统参数变化下是健壮的。混沌鞍的情况就是这样。例如，图2显示了受力阻尼摆的八个吸引域。八个吸引子仅仅只是周期不动点。吸引域边界上的混沌鞍引起了几何复杂性。吸引域随受力变化的发展可以在我们的YouTube视频中看到[4]。

Each manifestation or definition of chaos mentioned here comes with its own settings in which it can be verified, and with its own strengths and shortcomings, in terms of both numerical and theoretical uses. It is true that the non-equivalence of these mathematically precise formulations can be shown, but we choose to focus on the similarities, reiterating that the concept of chaos is too big for one single mathematical definition to suffice. We end by quoting a statement made during the controversy about Pluto as it was stripped of planethood, but which applies just as well to the chaos definition controversy: “Nature abhors a definition. Try to lock something into too small a box, and I guarantee nature will find an exception” [1]. 

这里所提到的混沌定义的每一种表现形式都有它自己的一些设置，在这些设置上，它可以被验证，当然在数值和理论上都有自己的长处和缺点。诚然，我们可以展示这些精确数学公式的非等价性，但我们选择关注相似之处，这里我们重申一下混沌的概念对单一的数学定义而言太大了，因此不能包含在单一的数学定义中。最后我们通过引用一段关于冥王星被剥夺行星地位的争论期间的声明来结束这篇文章，这同样也适用于混沌定义的争论：“自然厌恶定义。试着将一些东西锁进小盒子里，我保证大自然会发现例外[1]。

This article is a summary of our recent paper [5] and is based on the talk Evelyn Sander gave at the 2015 SIAM Conference on Applications of Dynamical Systems. Readers can find a more substantial reference list in the paper. 

这篇文章是我们最近论文[5]的一个总结，并基于Evelyn Sander在2015年SIAM Applications of Dynamical Systems会议上的讲话。读者可以在这篇论文中找到一个更丰富的参考文献。

**References**

[1] M. Brown, How I Killed Pluto and Why It Had It Coming, Random House, New York, 2010.

[2] B. Hunt and E. Ott, Defining chaos, Chaos, to appear: http://arxiv.org/abs/1501.07896. 

[3] H. Poincaré, New Methods of Celestial Mechanics, Vol. 13, American Institute of Physics, College Park, Maryland, 1993.

[4] E. Sander and J. Yorke, Pendulum gyrations, 2014; http://youtu.be/JyhaHyCvgw4 and http://math.gmu.edu/˜sander/EvelynSite/pendulum-gyrations.html.

[5] E. Sander and J. Yorke, The many facets of chaos, Internat. J. Bifur. Chaos Appl. Sci. Engrg., 25 (2015), 1530011-1-15. 