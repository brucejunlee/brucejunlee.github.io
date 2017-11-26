---
layout: post
title: "[SIAM NEWS] PAC: A Universal Framework for Learning?"
author: "李军"
categories: journal
tags: [siam, optimization, PAC]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

By <u>Ernest Davis</u>

October 01, 2013

[Ernest Davis is a professor of computer science at the Courant Institute of Mathematical Sciences, NYU.]

**BOOK REVIEW: Probably Approximately Correct.** By Leslie Valiant, Basic Books, New York, 2013, 208 pages, \$26.99.

In 2010, Leslie Valiant received the Turing Award, the “Nobel prize of computer science.” The citation mentioned a number of contributions, the best known of which is the theory of probably approximately correct (PAC) learning, which Valiant first proposed in the early 1980s. In his new book Probably Approximately Correct, Valiant discusses the theory of PAC learning and its applications to artificial intelligence; he also introduces a more specialized concept—“evolvable learning”—which, he claims, characterizes Darwinian evolution.

2010、莱斯利·瓦利安特获得图灵奖，计算机科学领域的“诺贝尔奖”。引文中提到了一些贡献，其中最著名的是可能近似正确的理论（PAC）学习，这勇敢的第一次提出在上世纪80年代初。在他的新书可能近似正确，勇敢的探讨了PAC学习理论及其在人工智能中的应用；他还引入了一个更专业的概念-“进化学习”，他声称，是达尔文进化。

PAC learning is an elegant framework that characterizes the objective and the computational difficulty of carrying out certain kinds of learning. Imagine a person or a computer program that is trying to determine the characteristics of mammals by viewing a sample of individual animals, each correctly labeled either “a mammal” or “not a mammal.” Suppose, as is likely, that the sample does not include any platypuses or echidnas. The learner might then come up with a rule like “hair, warm-blooded, suckles their young, live-bearing.” Although not quite correct, because platypuses and echidnas are mammals that lay eggs, this rule is approximately correct, because it works correctly for every animal except platypuses and echidnas.

PAC学习是一个优雅的框架，它的特点是目标和计算困难，进行某些类型的学习。想象一下，一个人或一个计算机程序，试图通过个体动物样本确定哺乳动物的特性，每个正确的标签是“哺乳动物”或“不是哺乳动物。”假设，是有可能的，这样不包括任何鸭嘴兽和针鼹。学生可能会想出一个规则”的头发，热血，吮吸他们的年轻，生活的承载。”虽然不完全正确，因为鸭嘴兽和针鼹是产卵的哺乳动物，这一规则大致是正确的，因为它除了鸭嘴兽和针鼹正确工作的每一个动物。

Given a large enough random sample, can we develop a learning algorithm that always generates an approximately correct answer? No, because we could be very unlucky in the constitution of our sample. For instance, there is a small but non-zero chance that in a random sample of animals, all the mammals will be platypuses and echidnas. If so, the learner might reasonably posit the additional condition that mammals are egg-laying; that rule would not be approximately correct. So what we can hope for is an algorithm that is probably approximately correct—an algorithm that, given a random sample, will probably come up with a rule that is approximately correct.

给定一个足够大的随机样本，我们可以开发一个学习算法，总是产生一个近似正确的答案？不，因为我们在样品的构造上可能非常不走运。例如，有一个小但非零的机会，在一个随机样本的动物，所有的哺乳动物鸭嘴兽和针鼹会。如果是这样的话，学习者可以合理地假定哺乳动物产卵的附加条件，这一规则将不正确。因此，我们可以期望的是一个算法，它可能近似正确，一个随机样本的算法，可能会产生一个近似正确的规则。

One particularly elegant feature of PAC learning is that, because the same distribution is used in the “probably” and the “approximately,” the algorithm does not have to make any prior assumptions about the distribution used to select the sample. Consider, for example, an anomalous distribution over mammals that chooses platypuses and echidnas 99.9% of the time. If samples are being generated according to that distribution, the learner is likely to come up with a rule that requires mammals to be egg-laying. But now that rule is approximately correct, relative to this anomalous distribution.

PAC学习的一个特别优雅的特点是，由于在“可能”和“近似”中使用了相同的分布，该算法不必对用于选择样本的分布作出任何先验假设。考虑，例如，一个异常分布在哺乳动物鸭嘴兽和针鼹，选择99.9%的时间。如果根据这种分布产生样本，学习者很可能会提出一个规则，要求哺乳动物产卵。但现在这个规则与这个反常分布相对应是正确的。

Another attractive feature of the definition, from the standpoint of mathematical analysis, is that it provides a number of numerical parameters to play with. There is 1−δ, the accuracy of the rule; 1−ϵ, the probability of attaining an approximately correct rule; n, the number of samples; s, the size of an individual instance; and t, the running time. PAC-learnability is a property of a collection C of categories in some space of instances X; for example, the collection of all categories definable by a simple conjunction of unary properties like “warm-blooded and hairy and suckles-young.” The collection C is PAC-learnable if there is an algorithm that, given large enough values of n and t, will probably find an approximately correct definition of each category in C for any distribution over X and for arbitrarily small δ and ϵ. Finally, following standard practice in complexity theory, Valiant characterizes a problem as “tractable” if it is solvable by an algorithm whose running time is bounded by a polynomial function of the parameters. Thus, the collection C is efficiently PAC-learnable if the running time t and the number of samples n are bounded by a polynomial in 1/ϵ, 1/δ, and s. Valiant and other researchers have proved a rather small number of learning problems to be efficiently PAC-learnable.

从数学分析的观点来看，定义的另一个吸引人的特点是它提供了许多数值参数。有1−δ，规则的准确性；1−ϵ，达到一个近似正确规则的概率；N，样本数；S，一个人的实例的大小；和T，运行时间。PAC可学习在一些空间的情况下，X的一个集合C类的属性；例如，所有类别的一个简单的像“热血和毛茸茸的哺乳年轻一元属性共同定义的集合。“集合C是PAC可学习如果有一个算法，给定n和t大足够的价值，可能会发现任何分布在X C每个类别大致正确的定义和任意小的δ和ϵ。最后，根据复杂性理论中的标准实践，如果一个算法的运行时间是由参数的多项式函数所限定的，那么该问题的特征是“听话的”。因此，如果运行时间t和样品是有界的一个多项式1 /ϵ数集合C是有效的PAC可学习，1 /δ，S.英勇和其他研究人员已经证明学习问题是有效地PAC可学习的一个很小的数目。

--

Despite the title, the focus of Valiant’s book is not PAC learning, but rather a question motivated by Darwinian evolution: Is it plausible that life could have evolved to its current state within the time that the earth has existed, if the mechanism for evolution is Darwinian? Valiant approaches the analysis of this problem by identifying Darwinian evolution with a narrow class of algorithms called “statistical query” algorithms. Algorithms in this class can use only statistical information about the sample as a whole; they are not allowed to use information about individual instances. A class of learning problems is considered evolvable if it satisfies the conditions of PAC learning when the class of algorithms under consideration is limited to statistical query algorithms. The theory of evolvable learning is much more recent and less developed than the theory of PAC learning, but some theoretical results have been obtained.

尽管书名如此，但《勇敢的书》的重点不是PAC学习，而是达尔文进化论提出的一个问题：如果进化的机制是达尔文式的，那么生命是否可能在地球存在的时间里发展到现在的状态，这是合理的吗？他用一种被称为“统计查询”算法的狭义算法来识别达尔文进化论，以此来分析这个问题。这个类中的算法只能使用关于样本的统计信息，它们不允许使用有关单个实例的信息。一类学习问题被认为是进化如果满足了PAC学习条件时，考虑这类算法是有限的统计查询算法。进化理论的学习远比PAC学习理论更近的和欠发达，但一些已取得的理论成果。

Valiant applies this theory to the question of the plausibility of Darwinism as follows. The terrestrial environment confronts each species with the challenge of maximizing its “performance” (essentially its fitness). The adaptation of a species through evolution is conceptualized as the execution of a learning algorithm (Valiant calls this an “ecorithm”) to solve that problem. The terrestrial environment, indeed, has a collection of problems that it could set to the species, and the ecorithm must be such that the species will successfully use it to solve any problem in the collection. Valiant is not very explicit about the exact relation of the complexity classes to the theories of evolution. Presumably, if the class of problems set by the environment is found to be evolvable, then Darwinism is plausible; if the collection is PAC-learnable but not evolvable, then some other evolutionary mechanism, such as Lamarckianism, should be sought; if it is not even PAC-learnable, then we must fall back on intelligent design, or on the anthropic principle. This kind of analysis presumably could not distinguish an evolutionary theory that requires 40 million years from one that requires 4 billion years, but it might distinguish these theories from those requiring $10^{20,000}$ years.

勇敢地将这一理论应用于达尔文主义的合理性问题如下。陆地环境面对每一个物种的挑战是最大限度地发挥其“性能”（本质上是它的适应性）。一种通过进化适应的概念是一个学习算法的执行（英勇称这是一个“ecorithm”）来解决这个问题。陆地环境，事实上，有一个集合，它可以设置的种类问题，和ecorithm必须使物种将成功地利用它来解决集合中的任何问题。对于复杂性类与进化论的确切关系，他并不是很清楚。据推测，如果问题由环境类是进化，那么进化论是合理的；如果集合是PAC可学习但不可进化的，那么其他的进化机制，如Lamarckianism，应寻求；如果它甚至不是PAC可学习的，那么我们必须依靠智能设计，或对人择原理。这种分析大概无法区分一种进化理论，这种理论需要4000万年时间，而这一理论需要40亿年时间，但它可能将这些理论与那些需要10美元（20000千年）的理论区别开来。

I am not at all an expert, but it does not seem to me that Valiant makes a very cogent case that this is a useful abstract model for this question. To what extent is it reasonable to view adaptation as the execution of an algorithm, and specifically a statistical query algorithm? In particular, to what extent is this a reasonable view of the early stages in the emergence of life, the formation of self-replicating biological chemicals? To what extent is it reasonable to view the environment as potentially posing any of the problems in a collection, and to require that the ecorithm be able to solve all of them? How is one to find a characterization of the class of problems that the environment could potentially present? Moreover, the devil is very much in the details in this kind of analysis: Small changes to the formulation of a problem can make a large difference in its learnability. Unless the abstraction reflects reality with high fidelity, an analysis based on that abstraction may well be useless.

我根本不是一个专家，但在我看来，《勇敢者》并不是一个令人信服的例子，它是这个问题的一个有用的抽象模型。在何种程度上将适应性看作是一种算法的执行，特别是一种统计查询算法是合理的？特别是，这在多大程度上是对生命出现的早期阶段的合理看法，是自我复制的生物化学品的形成？到什么程度是合理的查看环境可能构成任何集合中存在的问题，并要求该ecorithm就能解决所有吗？怎样才能找到环境可能存在的一类问题的表征？此外，魔鬼是在这种分析的细节非常多：对这个问题，小的变化可以使其学习能力差异较大。除非抽象以高逼真度反映现实，否则基于这种抽象的分析很可能是无用的。

--
 
The book also includes an extended discussion of machine learning and artificial intelligence, although the view of machine learning is disappointingly narrow. PAC learning applies in a natural way to only a rather restricted, though very important, class of learning problems: learning categories from labeled data (“supervised” learning), in cases in which there is an exact definition (or at least arbitrarily good definitions). If PAC learning is to be viewed as a universal framework for learning, other forms of learning must then either be shoehorned into this form, declared unimportant, or ignored. Valiant does some of each. Most strikingly, he specifically denies that unsupervised learning (learning from unlabeled examples, as in grouping examples into clusters) is a useful concept in studying natural learning, though he concedes that it may have some value in machine learning. In one case an errant form of learning sneaks in behind Valiant’s back, when he remarks in passing, in a discussion of learning from positive examples, “We may have figured out that each animal belongs to one species.” On the whole, one suspects that the way we figured this out was by learning it, although the problem of learning propositions like “each animal belongs to one species” does not fit well into the framework of supervised learning of categories.\*

本书还包括一个扩展的讨论机器学习和人工智能，虽然机器学习的观点是非常狭隘的。PAC学习以一种自然的方式应用于一个非常受限但非常重要的类学习问题：从标记数据（“监督”学习）中学习类别，在有确切定义的情况下（或者至少是任意好的定义）。如果PAC学习被看作是学习的一种通用的框架，其他形式的学习必须被硬塞进这一形式，宣布不重要，或忽视。每一个都有勇气。最引人注目的是，他特别否认无监督学习（从未标记的示例中学习，例如将示例分组为集群）是研究自然学习的一个有用的概念，尽管他承认它在机器学习中可能有一定的价值。在一个案例中一个错误的学习形式时，在勇士的后面，当他说的过客，在一个学习正面的例子的讨论，我们可以发现，每一种动物都属于一个物种。总的来说，一个犯罪嫌疑人，我们发现这是通过学习它，虽然学习命题如“每一种动物都属于一种“问题不适合监督学习分类的框架。\*

PAC learning is only one of many general frameworks that have been proposed for learning, and in many ways, it is one of the most limited. Other frameworks include Bayesian learning, minimum description length learning, the Vapnik–Chervonenkis theory of learning, and classical frequentist statistics. V–C theory is mentioned in an endnote, the others not at all.

PAC学习只是为学习而提出的许多一般框架中的一种，在许多方面，它是最有限的。其他框架包括贝叶斯学习，最小描述长度的学习，学习的本质–维和理论和经典概率统计。V–C理论是在尾注中提到，其他人根本不。

PAC learning is an elegant and useful approach to a specific class of learning problems. I am doubtful that an approach of this kind is useful in characterizing evolution; it is certainly not a universal framework applicable to all forms of either natural or machine learning.

PAC学习是针对特定类学习问题的一种优雅而有用的方法。我怀疑这种方法是否有助于表征进化；它肯定不是适用于所有形式的自然或机器学习的通用框架。

\* An observer in a state of nature does not directly perceive species; he perceives animals, their features, and their behaviors. Species are a higher-order construct. Learning the proposition “each animal belongs to one species” involves determining that the class of animals is partitioned into categories, that features and behavior of two animals in the same category are generally much more similar than features and behavior of two animals in different categories, and that animals breed only within the same category.

一个自然状态的观察者不直接感知物种；他感知动物、它们的特征和它们的行为。物种是高阶结构。学习的命题“每一种动物属于一种“涉及到确定的动物类分类别、特征和两个动物行为在同一类别通常比特征和不同类别的两只动物行为的更相似，而动物品种在同一范畴。