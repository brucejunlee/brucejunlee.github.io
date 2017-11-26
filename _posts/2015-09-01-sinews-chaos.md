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

典型的动力系统可以有简单的轨迹，如稳定状态或周期或准周期轨道，也可以是混乱的。当简单的行为被很好地理解时，混乱被定义在许多不同的方式中，它使困惑和困难很难得到一个合理的答案：一个简单的问题：混沌的定义是什么？我们断言这是一个错误的问题。

Chaos does not have a satisfactory single mathematical definition, not because it is not a single mathematical concept, but rather because it has many mathematical manifestations in many different situations. In this regard, we are reminded of the 2500-year-old parable of the blind monks and the elephant. Each monk touches a different part of the elephant; a monk feeling a tusk thinks the elephant is a spear, while others encounter different manifestations of the elephant—a rope-like tail, perhaps, or column-like legs. When we observe a chaotic system, we are blind to the enormity of the concept and observe only a limited number of aspects of the system’s chaotic nature.

混沌没有一个令人满意的单一数学定义，并不是因为它不是一个单一的数学概念，而是因为它在许多不同的情况下有许多数学表现。在这方面，我们想起了2500年前的盲人僧侣和大象的寓言。每个和尚摸了大象的不同部分；一个和尚感觉图斯克认为大象是长矛，而其他人遇到的elephant-a绳一样的尾巴，也许不同的表现，或柱状腿。当我们观察到一个混沌系统时，我们对这个概念的严重性视而不见，只观察到系统混沌性质的有限个方面。

In this article we discuss a variety of the manifestations and mathematical definitions of chaos. Our underlying message is that although it is possible to find pairs of definitions, one of which indicates that a system is chaotic and the other that it is not, this phenomenon is the exception, rather than the rule. We conjecture that, typically, the different forms of chaos are equivalent.

在这篇文章中，我们讨论了混沌的各种表现形式和数学定义。我们的基本信息是，虽然有可能找到对定义，其中一个表明系统是混乱的，而另一个是不存在的，这种现象是例外，而不是规则。我们推测，通常情况下，不同形式的混沌是等价的。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-chaos-1.jpg)

Figure 1. A homoclinic tangle with the chaotic complexity described by Poincaré.

Arguably the earliest observation of mathematical chaos occurred in the context of Newtonian mechanics. Henri Poincaré wrote a proof of the stability of the solar system, a result for which he won a substantial prize from King Oscar II of Sweden in 1890. After the prize was awarded, Lars Edvard Phragmén pointed out a substantial omission: Poincaré had assumed that only simple behavior could occur in a situation in which, in fact, it is possible to have chaotic behavior and what is now known as a transverse homoclinic orbit. In particular, there is a Cantor set of points with the property that the trajectory through almost any one of them occasionally comes arbitrarily close to that steady state both forward and backward in time, but with large excursions along the way.

可以说，最早的数学混沌观测是在牛顿力学的背景下发生的。庞加莱é写太阳系的稳定性证明，因此为他赢得了大量的奖金从1890瑞典国王奥斯卡二世。在颁奖，Lars爱德华膜片éN指出一个重大的遗漏：Poincaré以为只有简单的行为可以发生在这一情况，事实上，它是可能的混沌行为，什么是现在被称为横向同宿轨道。特别是，有一个康托集的属性的轨迹，其中几乎任何一个偶尔会任意接近稳定状态的时间向前和向后，但沿途大游览。

Poincaré's proof of the stability of the solar system completely collapsed, and the question remains open today (although the high likelihood of the survival of the planets in their orbits has been verified numerically to the expected time of the sun’s demise). Poincaré then undertook a major rewrite of the paper, in the course of which he discovered the underlying complexity of dynamical systems. In his words, “If one seeks to visualize the pattern formed . . . a chain-link network of infinitely fine mesh . . . one will be struck by the complexity. . ., which I am not even attempting to draw” [3]. Thankfully, the existence of computers makes it possible to depict this situation (shown in Figure 1).

Poincaré证明太阳系的稳定性完全崩溃，和今天的问题仍然是开放的（虽然在他们的轨道的行星的生存可能性很高已验证数值到太阳的死亡时间）。Poincaré进行了重大修改，在这一过程中，他发现了动力系统的底层复杂性。用他的话来说，“如果一个人试图想象形成的模式。..无限细网格的链式网络。..一个人会被复杂性所打击。..我甚至没有试图画“[ 3 ]。幸运的是，计算机的存在使我们能够描述这种情况（如图1所示）。

Following this path of ideas, Stephen Smale showed in 1967 that even in a simple two-dimensional map known as a horseshoe map, one sees the same complexity as in transverse homoclinic orbits; in fact, horseshoe maps are embedded in any system containing a transverse homoclinic orbit. This aspect of chaos is useful when visualization is difficult but analysis is tractable, as for delay differential equations and partial differential equations. Chaos of this type can often be transient—that is, it cannot be observed through direct simulations of a trajectory or in physical experiments. Furthermore, the characterization is not quantitative.

沿着这条思路，Stephen Smale显示1967，即使在简单的二维地图称为马蹄形地图，一看到相同的复杂度在横向同宿轨道；事实上，马蹄映射嵌入含有横向同宿轨道的任何系统。当可视化困难时，这方面是有用的，但分析是易于处理的，如时滞微分方程和偏微分方程。这种类型的混沌通常是暂时的，即不能通过对弹道或物理实验的直接模拟来观察到。此外，表征不是定量的。

In the course of numerical experiments for models of two very different natural systems, Yoshisuke Ueda (in 1961) and Edward Lorenz (in 1963) observed a robust but highly irregular topology in the trajectories of the systems. This “fractal topology” is a hallmark of attracting chaotic systems known as strange attractors; their measurement has since been made more precise in the form of attractor-dimension calculations. A general definition of strange attractors is still lacking, however, except for the subtype of rank-one attractors. Transverse homoclinic orbits often play a key role in shaping the geometry of strange attractors, and these concepts have been rigorously shown to be tightly related in many subclasses of systems.

在两个非常不同的自然系统模型的数值实验的过程中，Yoshisuke Ueda（1961）和Edward Lorenz（1963）中观察到的系统轨迹强劲而高度不规则的拓扑结构。这种“分形拓扑”是吸引称为奇怪吸引子的混沌系统的一个标志，其测量一直以吸引子维数计算的形式变得更加精确。然而，除了一阶吸引子的亚型外，对奇异吸引子的一般定义仍然缺乏。横向同宿轨道在决定奇异吸引子的几何结构中起着关键作用，这些概念在许多子系统中得到了严格的证明。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-chaos-2.jpg)

Figure 2. Eight basins of attraction for the forced–damped pendulum. The geometric complexity of the basins results from the chaos on their boundaries.

Rather than providing full knowledge of a system, experiments often give rise to time-series data. In 1975, Jerry Gollub and Harry Swinney demonstrated that the time-series data from Taylor–Couette fluid flow experiments had the chaotic hallmark of a broad power spectrum. In fact, the closely related Lyapunov exponent is the current most commonly used metric for characterizing chaos; using added information about the behavior of nearby orbits, the Lyapunov exponent indicates the degree of stretching along solutions. For experimental high-dimensional chaos, it is not possible in general to observe this stretching. The concept of stretching also appears in the definition of scrambled sets of Li and Yorke. Aside from stretching, another way to measure chaos is the possession of positive entropy. If the number of “distinct” orbits of period n is proportional to $a^n$, then the entropy is proportional to log(a). As with chaos, there are a variety of types of entropy. Each of the above-mentioned concepts can be shown to be distinct, although they appear to overlap in all but rather extreme cases, as discussed in [2].

实验不是提供系统的全部知识，而是经常产生时间序列数据。1975，Jerry Gollub和Harry Swinney证明了泰勒–Couette流动实验的时间序列数据具有广泛的功率谱的混沌特征。事实上，密切相关的李雅普诺夫指数是目前最常用的表征混沌的指标；利用附加的关于附近轨道行为的信息，李雅普诺夫指数表示沿解的拉伸程度。对于实验高维混沌，一般不可能观察到这种拉伸。伸展的概念也出现在定义混沌集的李和Yorke。除了伸展，测量混沌的另一种方法是拥有正熵。如果周期n的“明显”轨道数与$ n n成正比，则熵与对数（a）成比例。与混沌一样，有各种各样的熵。上述的每一个概念可以被证明是不同的，尽管它们似乎在所有但极端的情况下重叠，如[ 2 ]中讨论的那样。

The importance of non-attracting chaos is often overlooked, as it cannot be seen either by direct simulation or experimental observation. This behavior, though not stable, can organize the underlying behavior of the system and can be robust under changes to the system parameters. Such is the case for chaotic saddles. Figure 2, for example, shows the basins of eight attractors for the forced–damped pendulum. The eight attractors are simply periodic and fixed points. The chaotic saddle on the boundary of the basins causes the geometric complexity. The progression of the basins as the forcing changes can be seen in our YouTube video [4]. 

非吸引混沌的重要性常常被忽略，因为它不能通过直接模拟或实验观察来观察。这种行为虽然不稳定，但是可以组织系统的基本行为，并且在系统参数变化的情况下是健壮的。混沌鞍的情况就是这样。例如，图2显示了强迫阻尼摆的八个吸引子的盆。八个吸引子简单地是周期性的和不动点。盆地边界上的混沌鞍引起几何复杂度。在我们YouTube视频中可以看到盆地的变化，如强迫变化[ 4 ]。

Each manifestation or definition of chaos mentioned here comes with its own settings in which it can be verified, and with its own strengths and shortcomings, in terms of both numerical and theoretical uses. It is true that the non-equivalence of these mathematically precise formulations can be shown, but we choose to focus on the similarities, reiterating that the concept of chaos is too big for one single mathematical definition to suffice. We end by quoting a statement made during the controversy about Pluto as it was stripped of planethood, but which applies just as well to the chaos definition controversy: “Nature abhors a definition. Try to lock something into too small a box, and I guarantee nature will find an exception” [1]. 

这里所提到的混沌的每一种表现形式或定义都有它自己的设置，在这一点上，它可以被验证，并且在数值和理论上都有自己的长处和缺点。诚然，这些精确的数学公式的非对等可以显示，但我们选择关注的相似之处，重申混沌的概念是一个单一的数学定义就够了太大。最后我们通过引用关于冥王星的争论在它被剥夺行星的声明，但这同样也适用于混沌定义的争论：“自然厌恶的定义。试着把东西锁在一个小盒子里，我保证大自然会发现一个例外[ 1 ]。

This article is a summary of our recent paper [5] and is based on the talk Evelyn Sander gave at the 2015 SIAM Conference on Applications of Dynamical Systems. Readers can find a more substantial reference list in the paper. 

这篇文章是我们最近的论文[ 5 ]的总结，并基于Evelyn Sander在2015届暹罗动力系统应用会议上的讲话。读者可以在报纸上找到更实质性的参考书目。

**References**

[1] M. Brown, How I Killed Pluto and Why It Had It Coming, Random House, New York, 2010.

[2] B. Hunt and E. Ott, Defining chaos, Chaos, to appear: http://arxiv.org/abs/1501.07896. 

[3] H. Poincaré, New Methods of Celestial Mechanics, Vol. 13, American Institute of Physics, College Park, Maryland, 1993.

[4] E. Sander and J. Yorke, Pendulum gyrations, 2014; http://youtu.be/JyhaHyCvgw4 and http://math.gmu.edu/˜sander/EvelynSite/pendulum-gyrations.html.

[5] E. Sander and J. Yorke, The many facets of chaos, Internat. J. Bifur. Chaos Appl. Sci. Engrg., 25 (2015), 1530011-1-15. 