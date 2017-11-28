---
layout: post
title: "[SIAM NEWS] Machine Learning and the Prospect of a Master Algorithm"
author: "李军"
categories: journal
tags: [siam, machine learning]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

By <u>Ernest Davis</u>

January 19, 2016

[Ernest Davis is a professor of computer science at the Courant Institute of Mathematical Sciences, NYU.]

**The Master Algorithm: How the Quest for the Ultimate Learning Machine Will Remake Our World. By Pedro Domingos, Basic Books, New York, 2015, 352 pages, \$29.99.**

Machine learning (ML) has suddenly become very hot. It feels like every week, a machine learning algorithm achieves a major advance in some exciting application; and every other day the popular media publishes exaggerated accounts of these advances, or breathless predictions of what the future has in store. Over the last thirty-five years, ML has gone from being a largely-abandoned niche area of artificial intelligence to a central paradigm within computer science. Machine learning completely dominates applications such as computer vision, speech understanding, and recommender systems in addition to all forms of natural language processing.

机器学习（Machine learning, ML）突然变得很热。好像每周，机器学习算法都会在一些令人兴奋的应用中取得重大进展；每隔一天，大众媒体就会对这些进展发表有些夸大的报道，或者对未来前景进行令人屏息的预测。在过去的三十五年间，ML已经从人工智能中一个几乎要被抛弃的领域变成了计算机科学中的一个中心范例。机器学习完全主导了计算机视觉、语音理解和除所有形式的自然语言处理外的推荐系统等应用。

Pedro Domingos’ book, The Master Algorithm, presents an introduction to the techniques of ML, written for a popular audience. It seems to be the first popular book on ML, so it is certainly an important contribution toward general understanding of this enormously important technology.

Pedro Domingos的书《The Master Algorithm》，给出了ML技术的一个导论，这是写给普通大众的。这似乎是第一本ML的通俗读物，所以它肯定对这一重要技术的一般理解作出了重要贡献。

Chapters 3-7 of Domingos’ book survey the five major approaches to supervised ML: symbolic, connectionist, evolutionary, probabilistic, and exemplar-based. Chapter 8 covers unsupervised learning and meta-learning. These chapters are well-written, clear, and balanced; Domingos carefully describes the intuitions behind each approach, the practical successes the approach has attained, its strengths, and its inherent weaknesses. The true believers in each of the approaches will undoubtedly complain that Domingos shortchanged their own approach and handled the other approaches much too politely. The author gives very clear accounts of overfitting and of “the curse of dimensionality,” the two great hazards of ML. He almost entirely avoids the use of mathematics.

Domingos的书中第3-7章概述了监督ML的五大方法：符号主义，联结学派，进化论，概率主义以及基于范例。第8章介绍了无监督学习和元学习。这些章节都写得很好，很清晰，也很均衡；Domingos仔细描述了每种方法背后的直观看法，已经获得的实践成功，优点以及内在缺点。每种方法的真正信徒无疑会抱怨Domingos亏待了他们自己的方法而对其他方法的处理又过于礼貌。作者对过拟合和“维数灾难”给出了非常清晰的说明，它们是ML的两个主要危害因素。他几乎完全避免使用数学。

At his best, Domingos can be extremely good. He offers sharp, insightful statements of points easily overlooked. For instance, he writes that, “The most important thing about an equation is all the quantities that don’t appear in it; once we know what the essentials are, figuring out how they depend on each other is often the easier part.” Overall, these six chapters are a fine introduction to the state of the art of ML.

Domingos真的做得非常棒。他对很容易被忽视的问题提供了尖锐而深刻的观点。例如，他写道：“一个方程最重要的是没有出现的那些量；一旦我们知道了什么是本质，弄清它们彼此是如何依赖的往往变得是更容易”。总之，这六章是目前ML的一个很好的导论。

If only Domingos had been content with that! Unfortunately he has other things in mind, and these seriously degrade the book’s overall quality. I found the prologue and chapters 1 and 2 so uncongenial that I almost didn’t make it to chapter 3, and my objections returned in full force upon reaching chapters 9 and 10.

要是Domingos对此满意就好了! 不幸的是，他内心还有一些其它东西，这些严重降低了书的整体质量。我发现序言和第1章、第2章非常不相宜以至于我很难进入第3章，我的反对意见一直持续到第9章、第10章。

In addition to explaining the actual state of the art, Domingos has two additional goals. The first, explicit in the book’s title, is to develop the idea of a “Master Algorithm” for machine learning, which will subsume all other forms of learning and be able to learn anything that can be learned, and to argue that Domingos’ own “Alchemy” system is a major step in that direction. The second objective, implicit but pervasive and very conspicuous, is to hype the present accomplishments and future impacts of ML as raucously as possible. In pursuit of this goal, the book is generally overwrought, sometimes seriously misleading or simply wrong, and occasionally really quite strange

除了解释目前实际情况，Domingos还有两个额外目标。第一，正如书名中显式给出的，是要建立一个机器学习“主算法”的思想，这将包括所有其他形式的学习，并且能学到任何可被学习的东西，也能证明Domingos自己的“炼金术”系统在这个方向上迈出了重要一步。第二，虽然很隐含但却是普遍的显眼的，是要尽量炒作ML目前的成就和未来的影响。为了这一目标，这本书通常过度紧张了，有时严重带有误导性或根本就是错误的，有时候也真的很奇怪。

For example, in presenting connectionist models, Domingos gets carried away with phase transitions and the idea of an S-curve, which he characteristically calls “the most important curve in the world.” He spends an entire page enumerating S-curves and phase transitions, including some very doubtful examples. Paradigm shifts in science and the fall of empires are supposedly S-curves. Falling in love, getting a job, and losing a job are allegedly phase transitions; clearly at this point “phase transition” just translates to “important change.”

例如，在介绍联结学派模型时，Domingos不能自已地讲到了相变和S型曲线（他称之为“世界上最重要的曲线”）的想法。他花了一整页列举S型曲线和相变，其中还包括一些非常有问题的例子。科学中的范式转移和帝国的没落据说都是S型曲线。坠入爱河，找工作和失业据说都是相变；显然，这里的“想变”仅仅指的是“重要的变化”。

Domingos’ view of computerization’s past impact on science is wildly exaggerated. He writes that “If computers hadn’t been invented, science would have ground to a halt in the second half of the twentieth century.” It certainly would have been impeded, and some discoveries would have been impossible, but it seems safe to say that only a small fraction of scientific discoveries before about 1990 relied critically on computers. 

Domingos的电脑化过去对科学影响的观点是极其夸大的。他写道，“如果电脑没有被发明，科学将在二十世纪下半叶陷入停顿”。它肯定会受阻碍，也将得不到一些发现，但似乎可以这样说，大概1990年前只有很少一部分科学发现严重依赖于电脑。

Moreover, Domingos’ view of the future impact of the Master Algorithm is fantasy: “Science today is thoroughly balkanized, a Tower of Babel where each subcommunity can see only into a few adjacent subcommunities.” He then proceeds to state that the Master Algorithm would offer a unified perspective of all science, one that could even lead to a new theory of everything. Even if a Master Algorithm could derive each scientific theory from data, there is no reason to expect that it would provide a unifying view, rather than a collection of separate theories. Domingos continues by saying that “The Master Algorithm is the germ of every theory: all we need to add to it to obtain theory X is the minimum amount of data required to induce it. (In the case of physics, that would be the results of perhaps a few hundred key experiments).” That estimate is certainly too low by at least a factor of one hundred.

此外，Domingos对主算法的未来影响的观点也是不合实际的：“今天的科学是一个彻底的地缘化的巴别塔，每个社群只能看到一些相邻社群的信息”。他接着指出，主算法将为所有科学提供一个统一的观点，它甚至可能导致一种万物新理论。虽然主算法可以从数据中导出每一个科学理论，但我们也没有理由期望它能提供一个统一的观点而非一群单独理论。Domingos接着说，“主算法是每个理论的萌芽：我们需要给它添加以获得理论X的只是所诱导的最小数据量。（在物理中，这可能是几百个关键实验的结果）”。通过至少一百个因素中的一个来看，这个估计肯定太低了。

In chapter 10, Domingos presents his vision of the future. Some aspects of this seem reasonable; in particular, I agree with his belief that there is no danger of computers developing their own goals `a la Skynet and exterminating or enslaving us. Other thoughts, however, appear both weird and dreary, like the following Baudrillardesque nightmare: “In this rapidly approaching future, you’re not going to be the only one with a ‘digital half’ doing your bidding twenty-four hours a day. Everyone will have a detailed model of him- or herself, and these models will talk to each other all the time.”

在第10章中，Domingos阐述了他对未来的憧憬。一些方面看起来是合理的；特别是，他认为，建立它们自己的目标（即天网）并消灭或奴役我们的计算机一点也不危险，这一点我很认同。然而其它的想法似乎也很古怪沉闷，如下面的baudrillardesque噩梦：“在即将到来的未来，你不会是唯一一个一天二十四小时投标的‘半数字人’。每个人都有他/她自己的精细模型，这些模型会一直彼此沟通”。

He proceeds to give examples for how this will happen: “If company X is looking to hire, its model will interview your model. It will be a lot like a real, flesh-and-blood interview . . . but it will take only a fraction of a second . . . Same with dating.” [^1] Domingos does not explain why a company would trust that your avatar is an accurate portrayal of yourself, nor why the company should not hire the avatar instead, since it presumably does the same things thousands of times faster.

他继续举例说明这是如何发生的：“如果X公司想招人，它的模型将面试你的模型。这很像一次真实的、有血有肉的面试...但只需要几分之一秒...约会同样如此”。Domingos没有解释为什么公司会相信你的头像是你自己的一个精确刻画，相反也没解释为什么公司不应该招头像，因为它大概上千倍快地做相同事情。

The issue most important to Domingos is his Master Algorithm conjecture: “All knowledge — past, present, and future — can be derived from data by a single, universal learning algorithm.” In chapter 2, he presents many different arguments for the hypothesis, drawing evidence from fields such as neuroscience, evolution, physics, statistics, and computer science.

对Domingos最重要的事情是他的主算法猜想：“一切知识（过去、现在和未来）都可以通过一个简单的通用学习算法从数据中导出”。在第2章中，他提出了该假说的许多不同论点，证据来自神经科学、进化论、物理、统计以及计算机科学等领域。

In my opinion, these assertions are incoherent. The different arguments rely on varied interpretations of the terms “data,” “single,” “universal,” “learning,” and “algorithm,” and therefore point in different directions. For instance, Domingos bases his case for the neuroscience perspective on the uniform structure of the cortex. Yet in chapter 9, he is willing to consider a Master Algorithm which calls on a variety of very different algorithms and combines their votes. The uniform structure of the cortex is, if anything, evidence against a Master Algorithm of this kind. The kind of algorithm he proposes would be consistent with a brain that combines pieces of very diverse structures.

在我看来，这些断言是无条理的。不同论点依赖于对“数据”、“简单”、“通用”、“学习”和“算法”等术语的不同解释，因此它指向不同的方向。例如，Domingos依据的是他对皮层均匀结构的神经科学的看法。然而，在第9章中，他想考虑一个主算法，它调用各种不同的算法，并结合它们的投票结果。如果有的话，那么皮层的均匀结构就是反对这种主算法的证据。他提出的这种算法与结合许多不同结构的大脑是一致的。

As Domingos himself observes, the Master Algorithm is very unlike existing trends in machine learning, which generally involve highly-handcrafted algorithms for fairly narrowly-defined tasks. Indeed, it is unlike anything that we have seen in computer science. Domingos’ argument from the computer science viewpoint rests on the fact that the many NP-complete problems are, in a certain sense, actually the same problem. However, it seems to me that this points in exactly the opposite direction. NP-complete problems are all reducible to the problem of Boolean satisfiability, but there are, probably, tens of thousands of different algorithms for solving specific NP-complete problems, depending on the specifics of the problem and on the desired features of the solution and the algorithm.

正如Domingos自己注意到的，主算法是非常不同于机器学习现有的趋势，这通常涉及在比较狭义的任务中高度手工的算法。事实上，它与我们在计算机科学中所看到的有所不同。Domingos来自计算机科学角度的论点基于这样一个事实，即在某种意义上，许多NP完全问题其实是同一个问题。然而，在我看来，这完全是相反方向。NP完全问题都可以归约为布尔可满足问题，但求解特定的NP完全问题很可能有成千上万种不同的算法，这取决于具体的问题以及解和算法的期望特征。

The Master Algorithm does a fine job of explaining machine learning techniques to the general public. Unfortunately, it is also often extremely misleading.  If you have a lay friend who wants to understand ML, by all means recommend it, but do so with a warning.

《The Master Algorithm》一书在向一般公众讲解机器学习技术方面做得很好。不幸的是，它也常常极具误导性。如果你有一个想理解ML的外行朋友，一定要向他推荐这本书，但你也需要给他一点警告。

[^1]: Felicia Day’s “Do you wanna date my avatar?” (2009) is a particularly insightful discussion of this issue.