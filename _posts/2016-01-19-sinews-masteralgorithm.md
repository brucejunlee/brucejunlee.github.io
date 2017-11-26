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

**The Master Algorithm: How the Quest for the Ultimate Learning Machine Will Remake Our World.** By Pedro Domingos, Basic Books, New York, 2015, 352 pages, $29.99.

Machine learning (ML) has suddenly become very hot. It feels like every week, a machine learning algorithm achieves a major advance in some exciting application; and every other day the popular media publishes exaggerated accounts of these advances, or breathless predictions of what the future has in store. Over the last thirty-five years, ML has gone from being a largely-abandoned niche area of artificial intelligence to a central paradigm within computer science. Machine learning completely dominates applications such as computer vision, speech understanding, and recommender systems in addition to all forms of natural language processing.

机器学习（ML）突然变得非常热门。每一周，机器学习算法都会在一些令人兴奋的应用程序中取得重大进展；每隔一天，大众媒体就会对这些进展发表夸大的报道，或者对未来的前景进行令人屏息的预测。在过去的三十五年中，ML已经从人工智能的一个主要被遗弃的利基领域变成了计算机科学中的一个中心范例。除了所有形式的自然语言处理外，机器学习完全支配着计算机视觉、语音理解和推荐系统等应用。

Pedro Domingos’ book, The Master Algorithm, presents an introduction to the techniques of ML, written for a popular audience. It seems to be the first popular book on ML, so it is certainly an important contribution toward general understanding of this enormously important technology.

Pedro Domingos的书，掌握算法，提出了ML的技术介绍，为大众读者写。这似乎是第一本受欢迎的关于ML的书，所以它肯定是对这一非常重要的技术的一般理解的重要贡献。

Chapters 3-7 of Domingos’ book survey the five major approaches to supervised ML: symbolic, connectionist, evolutionary, probabilistic, and exemplar-based. Chapter 8 covers unsupervised learning and meta-learning. These chapters are well-written, clear, and balanced; Domingos carefully describes the intuitions behind each approach, the practical successes the approach has attained, its strengths, and its inherent weaknesses. The true believers in each of the approaches will undoubtedly complain that Domingos shortchanged their own approach and handled the other approaches much too politely. The author gives very clear accounts of overfitting and of “the curse of dimensionality,” the two great hazards of ML. He almost entirely avoids the use of mathematics.

Domingos的书调查监督ML五大方法3-7章：象征性的联结，进化的概率，并基于样例。第8章介绍无监督学习和元学习。这些章节都写得很好，清晰，和平衡；Domingos仔细描述了每种方法的直觉背后，实际成功的方法了，它的力量，和其固有的弱点。在每个方法的真正信徒无疑会抱怨Domingos欺骗了自己的方法和处理其他方法太有礼貌。作者给出了非常清晰的账目和过“维数灾难，”他几乎完全避免了为数学应用的两大危害。

At his best, Domingos can be extremely good. He offers sharp, insightful statements of points easily overlooked. For instance, he writes that, “The most important thing about an equation is all the quantities that don’t appear in it; once we know what the essentials are, figuring out how they depend on each other is often the easier part.” Overall, these six chapters are a fine introduction to the state of the art of ML.

在他的最好的，多明戈斯可以非常好。他提供了尖锐而深刻的观点，容易被忽视。例如，他写道：“一个等式最重要的是它没有出现的所有数量；一旦我们知道了什么是本质，弄清它们是如何相互依赖的往往是更容易的部分。”总的来说，这六章是对ML.艺术状态的一个很好的介绍。

If only Domingos had been content with that! Unfortunately he has other things in mind, and these seriously degrade the book’s overall quality. I found the prologue and chapters 1 and 2 so uncongenial that I almost didn’t make it to chapter 3, and my objections returned in full force upon reaching chapters 9 and 10.

If only Domingos had been content with that! 不幸的是，他脑子里有其他的东西，这些严重降低了书的整体质量。我发现序言和1和2这样不协调的，我几乎没能第3章，和我的意见完全归还力到达章9和10。

In addition to explaining the actual state of the art, Domingos has two additional goals. The first, explicit in the book’s title, is to develop the idea of a “Master Algorithm” for machine learning, which will subsume all other forms of learning and be able to learn anything that can be learned, and to argue that Domingos’ own “Alchemy” system is a major step in that direction. The second objective, implicit but pervasive and very conspicuous, is to hype the present accomplishments and future impacts of ML as raucously as possible. In pursuit of this goal, the book is generally overwrought, sometimes seriously misleading or simply wrong, and occasionally really quite strange

除了解释艺术的现状，Domingos有两个额外的目标。第一，这本书的标题明确，是建立一个“大师”算法的机器学习的思想，这将包括所有其他形式的学习，能学到东西，是可以学习的，并认为Domingos的“炼金术”系统是在这个方向迈出的重要一步。第二目的，隐而普遍非常显眼，是炒作目前的成就和未来的影响尽可能地ML。在追求这一目标，本书通常是过度紧张，有时严重的误导或者根本就是错误的，有时候真的很奇怪

For example, in presenting connectionist models, Domingos gets carried away with phase transitions and the idea of an S-curve, which he characteristically calls “the most important curve in the world.” He spends an entire page enumerating S-curves and phase transitions, including some very doubtful examples. Paradigm shifts in science and the fall of empires are supposedly S-curves. Falling in love, getting a job, and losing a job are allegedly phase transitions; clearly at this point “phase transition” just translates to “important change.”

例如，在介绍联结模型，Domingos得到了相变和S曲线的想法，他都称之为“世界上最重要的曲线。”他花了一整页列举S曲线和相变，包括一些非常可疑的例子。在科学的范式转变与帝国的没落是S曲线。坠入爱河，找工作，失去工作，据说是阶段性转变；显然，在这一点上，“过渡阶段”只是转化为“重要的变化”。

Domingos’ view of computerization’s past impact on science is wildly exaggerated. He writes that “If computers hadn’t been invented, science would have ground to a halt in the second half of the twentieth century.” It certainly would have been impeded, and some discoveries would have been impossible, but it seems safe to say that only a small fraction of scientific discoveries before about 1990 relied critically on computers. 

多明戈斯的计算机化的过去的影响，科学的观点是夸大。他写道，“如果电脑没有被发明，科学将有地面在第二十世纪下半叶停止。“它肯定将受到阻碍，而有些发现是不可能的，但似乎可以说，只有一小部分的科学发现在大约1990依赖严重的电脑上。

Moreover, Domingos’ view of the future impact of the Master Algorithm is fantasy: “Science today is thoroughly balkanized, a Tower of Babel where each subcommunity can see only into a few adjacent subcommunities.” He then proceeds to state that the Master Algorithm would offer a unified perspective of all science, one that could even lead to a new theory of everything. Even if a Master Algorithm could derive each scientific theory from data, there is no reason to expect that it would provide a unifying view, rather than a collection of separate theories. Domingos continues by saying that “The Master Algorithm is the germ of every theory: all we need to add to it to obtain theory X is the minimum amount of data required to induce it. (In the case of physics, that would be the results of perhaps a few hundred key experiments).” That estimate is certainly too low by at least a factor of one hundred.

此外，Domingos大师的算法的未来影响的观点是：“今天的科学幻想彻底四分五裂，通天塔，每个机构只能看到为数个相邻。”他接着指出，掌握算法将提供所有科学统一的角度来看，这甚至可能导致一种新的理论的东西。即使主算法可以从数据中推导出每一个科学理论，也没有理由期望它能提供一个统一的观点，而不是一个单独的理论集合。多明戈斯继续说，”大师算法是每个思想的萌芽：我们需要给它添加获得X理论所诱导的最小数据量。（在物理学方面，这可能是几百个关键实验的结果），“这个估计肯定太低了，至少是一百的一个因素。

In chapter 10, Domingos presents his vision of the future. Some aspects of this seem reasonable; in particular, I agree with his belief that there is no danger of computers developing their own goals `a la Skynet and exterminating or enslaving us. Other thoughts, however, appear both weird and dreary, like the following Baudrillardesque nightmare: “In this rapidly approaching future, you’re not going to be the only one with a ‘digital half’ doing your bidding twenty-four hours a day. Everyone will have a detailed model of him- or herself, and these models will talk to each other all the time.”

在10章中，Domingos阐述了自己对未来的憧憬。这一些方面看起来是合理的；特别是，我同意他的观点，没有计算机的发展自己的目标` La天网和灭绝或奴役我们的危险。然而其他的想法，，出现怪异而沉闷，像下面的baudrillardesque噩梦：“在这个迅速到来的未来，你不会是唯一一个数字的一半做一天二十四小时你的投标。每个人都会有自己的详细模型，这些模型会一直互相交谈。

He proceeds to give examples for how this will happen: “If company X is looking to hire, its model will interview your model. It will be a lot like a real, flesh-and-blood interview . . . but it will take only a fraction of a second . . . Same with dating.” 1 Domingos does not explain why a company would trust that your avatar is an accurate portrayal of yourself, nor why the company should not hire the avatar instead, since it presumably does the same things thousands of times faster.

他继续举例说明这是如何发生的：“如果X公司想雇佣，它的模型将访问你的模型。这将非常像一次真实的、血肉的访谈。..但只需要一小部分。..同样的约会”。1多明戈斯没有解释为什么公司会相信你的头像是一个自己的准确的描述，也不知道为什么公司不应该雇的化身，相反，由于它大概是几千倍的速度相同的东西。

The issue most important to Domingos is his Master Algorithm conjecture: “All knowledge — past, present, and future — can be derived from data by a single, universal learning algorithm.” In chapter 2, he presents many different arguments for the hypothesis, drawing evidence from fields such as neuroscience, evolution, physics, statistics, and computer science.

Domingos的问题最重要的是他的主人算法猜想：”一切知识的过去，现在和未来可以从由一个单一的数据，通用学习算法”。在2章中，他提出了许多不同的假说的争论，从诸如神经科学、进化、物理、统计、绘图的证据，与计算机科学。

In my opinion, these assertions are incoherent. The different arguments rely on varied interpretations of the terms “data,” “single,” “universal,” “learning,” and “algorithm,” and therefore point in different directions. For instance, Domingos bases his case for the neuroscience perspective on the uniform structure of the cortex. Yet in chapter 9, he is willing to consider a Master Algorithm which calls on a variety of very different algorithms and combines their votes. The uniform structure of the cortex is, if anything, evidence against a Master Algorithm of this kind. The kind of algorithm he proposes would be consistent with a brain that combines pieces of very diverse structures.

在我看来，这些断言是不连贯的。不同的论点依赖于对“数据”、“单”、“通用”、“学习”和“算法”等术语的不同解释，因此指向不同的方向。例如，Domingos根据他的情况对皮层结构均匀的神经科学的研究视角。然而，在第9章中，他愿意考虑一个主算法，它调用各种不同的算法，并结合他们的投票。皮层的均匀结构，如果有的话，就是反对这种主算法的证据。他提出的这种算法与一种结合了许多不同结构的大脑是一致的。

As Domingos himself observes, the Master Algorithm is very unlike existing trends in machine learning, which generally involve highly-handcrafted algorithms for fairly narrowly-defined tasks. Indeed, it is unlike anything that we have seen in computer science. Domingos’ argument from the computer science viewpoint rests on the fact that the many NP-complete problems are, in a certain sense, actually the same problem. However, it seems to me that this points in exactly the opposite direction. NP-complete problems are all reducible to the problem of Boolean satisfiability, but there are, probably, tens of thousands of different algorithms for solving specific NP-complete problems, depending on the specifics of the problem and on the desired features of the solution and the algorithm.

正如Domingos自己指出的，主算法是非常不同于机器学习现有的趋势，这通常涉及高度手工算法比较狭义的任务。事实上，它与我们在计算机科学中所看到的不同。多明戈斯的论点，从计算机科学的观点建立在事实上，许多NP完全问题，在一定意义上，其实同样的问题。然而，在我看来，这完全是相反的方向。NP完全问题都可以归结为布尔可满足性问题，但有可能，有成千上万种不同的算法来求解特定的NP完全问题，具体取决于问题的细节和解决方案和算法的期望特征。

The Master Algorithm does a fine job of explaining machine learning techniques to the general public. Unfortunately, it is also often extremely misleading.  If you have a lay friend who wants to understand ML, by all means recommend it, but do so with a warning.

主算法在向一般公众讲解机器学习技术方面做得很好。不幸的是，它也常常极具误导性。如果你有一个想理解ML的外行朋友，一定要推荐它，但是要有警告。

1 Felicia Day’s “Do you wanna date my avatar?” (2009) is a particularly insightful discussion of this issue.

1菲丽西亚·戴的“你想和我的阿凡达约会吗？”“（2009）对这个问题进行了特别精辟的讨论。