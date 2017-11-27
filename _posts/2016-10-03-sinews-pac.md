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

**BOOK REVIEW: Probably Approximately Correct. By Leslie Valiant, Basic Books, New York, 2013, 208 pages, \$26.99.**

In 2010, Leslie Valiant received the Turing Award, the “Nobel prize of computer science.” The citation mentioned a number of contributions, the best known of which is the theory of probably approximately correct (PAC) learning, which Valiant first proposed in the early 1980s. In his new book Probably Approximately Correct, Valiant discusses the theory of PAC learning and its applications to artificial intelligence; he also introduces a more specialized concept—“evolvable learning”—which, he claims, characterizes Darwinian evolution.

2010年，Leslie Valiant获得图灵奖，该奖被称为“计算机科学界的诺贝尔奖”。颁奖词中提到了大量贡献，其中最著名的是可能近似正确（probably approximately correct，PAC）学习，Valiant在上世纪80年代初第一次提出该理论。在他的新书《Probably Approximately Correct》中，Valiant探讨了PAC学习理论及其在人工智能中的应用；他还引入了一个更专业的概念“进化学习”，他声称，这可以刻画达尔文进化论。

PAC learning is an elegant framework that characterizes the objective and the computational difficulty of carrying out certain kinds of learning. Imagine a person or a computer program that is trying to determine the characteristics of mammals by viewing a sample of individual animals, each correctly labeled either “a mammal” or “not a mammal.” Suppose, as is likely, that the sample does not include any platypuses or echidnas. The learner might then come up with a rule like “hair, warm-blooded, suckles their young, live-bearing.” Although not quite correct, because platypuses and echidnas are mammals that lay eggs, this rule is approximately correct, because it works correctly for every animal except platypuses and echidnas.

PAC学习是一个优雅的框架，它可以刻画进行某类学习的目标和计算难度。想象一个人或一个计算机程序，它／他正试图通过看一些动物样本来确定哺乳动物的特性，每个样本都正确标有“是哺乳动物”或“不是哺乳动物”。有可能假设，样本中不包括任何鸭嘴兽和针鼹鼠。然后学习者可能会得出一个像“有毛发、恒温、哺乳、胎生”的规则。虽然不完全正确，因为鸭嘴兽和针鼹鼠是卵生哺乳动物，但这一规则是近似正确的，因为它对除鸭嘴兽和针鼹鼠外的每一个哺乳动物都适用。

Given a large enough random sample, can we develop a learning algorithm that always generates an approximately correct answer? No, because we could be very unlucky in the constitution of our sample. For instance, there is a small but non-zero chance that in a random sample of animals, all the mammals will be platypuses and echidnas. If so, the learner might reasonably posit the additional condition that mammals are egg-laying; that rule would not be approximately correct. So what we can hope for is an algorithm that is probably approximately correct—an algorithm that, given a random sample, will probably come up with a rule that is approximately correct.

给定一个足够大的随机样本，我们可以开发一个总能产生近似正确答案的学习算法吗？不能，因为我们在样本的构造上可能非常不走运。例如，存在一个非常小但非零的可能，在一个随机的动物样本中，所有的哺乳动物都是鸭嘴兽和针鼹鼠。如果是这样的话，学习者可以会另外合理地假定哺乳动物是卵生的，但这一规则不是近似正确的。因此，我们希望的是一个PAC算法，也就是给定一个随机样本，我们可能会产生一个近似正确的规则。

One particularly elegant feature of PAC learning is that, because the same distribution is used in the “probably” and the “approximately,” the algorithm does not have to make any prior assumptions about the distribution used to select the sample. Consider, for example, an anomalous distribution over mammals that chooses platypuses and echidnas 99.9% of the time. If samples are being generated according to that distribution, the learner is likely to come up with a rule that requires mammals to be egg-laying. But now that rule is approximately correct, relative to this anomalous distribution.

PAC学习的一个特别优秀的特点是由于在“可能”和“近似”中使用了相同的分布，该算法不必对用于样本选择的分布作任何先验假设。例如，考虑一个99.9%的时间都选择哺乳动物中的鸭嘴兽和针鼹鼠的反常分布。如果根据那种分布产生样本，学习者很可能会得出一个哺乳动物卵生的规则。但是现在相对于这个反常分布而言，那个规则是近似正确的。

Another attractive feature of the definition, from the standpoint of mathematical analysis, is that it provides a number of numerical parameters to play with. There is 1−δ, the accuracy of the rule; 1−ϵ, the probability of attaining an approximately correct rule; n, the number of samples; s, the size of an individual instance; and t, the running time. PAC-learnability is a property of a collection C of categories in some space of instances X; for example, the collection of all categories definable by a simple conjunction of unary properties like “warm-blooded and hairy and suckles-young.” The collection C is PAC-learnable if there is an algorithm that, given large enough values of n and t, will probably find an approximately correct definition of each category in C for any distribution over X and for arbitrarily small δ and ϵ. Finally, following standard practice in complexity theory, Valiant characterizes a problem as “tractable” if it is solvable by an algorithm whose running time is bounded by a polynomial function of the parameters. Thus, the collection C is efficiently PAC-learnable if the running time t and the number of samples n are bounded by a polynomial in 1/ϵ, 1/δ, and s. Valiant and other researchers have proved a rather small number of learning problems to be efficiently PAC-learnable.

从数学分析的观点来看，定义另一个诱人的特点是它提供了许多数值参数。有1−δ（规则的准确性）；1−ϵ（达到一个近似正确规则的概率）；n（样本数）；s（单个实例的大小）以及t（运行时间）等。PAC可学习性是实例X的某个空间中类别集合C的一个属性；例如，通过像“恒温、有毛发、哺乳”这样的单元属性的简单连接定义的所有类别集合。如果给定足够大的n和t值，对于X上的任何分布以及任意小的δ和ϵ，都存在一个可能找到C中每个类别近似正确定义的算法，那么集合C就是PAC可学习的。最后，根据复杂性理论中的标准实践方法，Valiant描述了这样一个问题，如果这个问题可以通过一个运行时间受限于参数的多项式函数的算法求解，那么该问题的特征就是“易处理的”。因此，如果运行时间t和样本数n受限于关于1/ϵ、1/δ以及s的一个多项式，那么集合C就是高效PAC可学习的。Valiant和其他研究人员已经证明了一些学习问题是高效PAC可学习的。

--

Despite the title, the focus of Valiant’s book is not PAC learning, but rather a question motivated by Darwinian evolution: Is it plausible that life could have evolved to its current state within the time that the earth has existed, if the mechanism for evolution is Darwinian? Valiant approaches the analysis of this problem by identifying Darwinian evolution with a narrow class of algorithms called “statistical query” algorithms. Algorithms in this class can use only statistical information about the sample as a whole; they are not allowed to use information about individual instances. A class of learning problems is considered evolvable if it satisfies the conditions of PAC learning when the class of algorithms under consideration is limited to statistical query algorithms. The theory of evolvable learning is much more recent and less developed than the theory of PAC learning, but some theoretical results have been obtained.

尽管书名如此，但Valiant书的重点不是PAC学习，而是受达尔文进化论启发的一个问题：如果进化的机制是达尔文式的，那么生命从地球存在至今进化到现在的状态是合理的吗？Valiant通过将达尔文进化论和一小类被称为“统计查询”的算法联系起来，以此来分析这个问题。这类算法只使用全部样本的统计信息，不允许使用单个实例的信息。如果目前考虑的这类算法受限于统计查询算法时满足PAC学习条件，那么这类学习问题被认为是可进化的。进化学习理论只是最近才提出的，远没有PAC学习理论发展得好，但也取得了一些理论成果。

Valiant applies this theory to the question of the plausibility of Darwinism as follows. The terrestrial environment confronts each species with the challenge of maximizing its “performance” (essentially its fitness). The adaptation of a species through evolution is conceptualized as the execution of a learning algorithm (Valiant calls this an “ecorithm”) to solve that problem. The terrestrial environment, indeed, has a collection of problems that it could set to the species, and the ecorithm must be such that the species will successfully use it to solve any problem in the collection. Valiant is not very explicit about the exact relation of the complexity classes to the theories of evolution. Presumably, if the class of problems set by the environment is found to be evolvable, then Darwinism is plausible; if the collection is PAC-learnable but not evolvable, then some other evolutionary mechanism, such as Lamarckianism, should be sought; if it is not even PAC-learnable, then we must fall back on intelligent design, or on the anthropic principle. This kind of analysis presumably could not distinguish an evolutionary theory that requires 40 million years from one that requires 4 billion years, but it might distinguish these theories from those requiring 10<sup>20,000</sup> years.

下面，Valiant将这一理论应用于达尔文主义的合理性问题。陆地环境中每一个物种都面对最大限度发挥其“性能”的挑战（本质上就是适应性）。进化中的物种适应性被概念化成求解该问题的一个学习算法（Valiant称之为“生态法则”）的执行。事实上，陆地环境的确有一类针对物种设定的问题集，生态法则必须如此物种才能成功利用它来解决集合中的任何问题。Valiant并没有明确说明复杂类和进化论之间的精确关系。大概是这样的，如果由环境设定的这类问题是可进化的，那么达尔文进化论便是合理的；如果集合是PAC可学习的但不是可进化的，那么我们需要寻找一些其它的如Lamarckianism等进化机制；如果它甚至不是PAC可学习的，那么我们必须求助于智能设计或人择原理。但这种分析大概无法区分需要4千万年的进化论和需要40亿年的进化论，但它或许能将这些理论与需要10<sup>20,000</sup>年的理论区分开。

I am not at all an expert, but it does not seem to me that Valiant makes a very cogent case that this is a useful abstract model for this question. To what extent is it reasonable to view adaptation as the execution of an algorithm, and specifically a statistical query algorithm? In particular, to what extent is this a reasonable view of the early stages in the emergence of life, the formation of self-replicating biological chemicals? To what extent is it reasonable to view the environment as potentially posing any of the problems in a collection, and to require that the ecorithm be able to solve all of them? How is one to find a characterization of the class of problems that the environment could potentially present? Moreover, the devil is very much in the details in this kind of analysis: Small changes to the formulation of a problem can make a large difference in its learnability. Unless the abstraction reflects reality with high fidelity, an analysis based on that abstraction may well be useless.

我不是专家，但在我看来，Valiant给出了一个非常中肯的情况，它是这个问题一个非常有用的抽象模型。在何种程度上将适应性视作一种算法，特别是一种统计查询算法的执行是合理的呢？特别是，这在多大程度上是对生命出现早期，即自复制生物化学物质的形成的合理看法？这在多大程度上将环境视作可能构成集合中任何问题，并需要生态法则才能解决这些问题呢？怎样才能找到环境中潜在的这类问题的表征呢？此外，在这种分析细节中有很多讨厌的东西：对问题形成的微小变化都可能使其学习能力差异较大。除非抽象高度反映现实，否则基于这种抽象的分析将很可能无用。

--
 
The book also includes an extended discussion of machine learning and artificial intelligence, although the view of machine learning is disappointingly narrow. PAC learning applies in a natural way to only a rather restricted, though very important, class of learning problems: learning categories from labeled data (“supervised” learning), in cases in which there is an exact definition (or at least arbitrarily good definitions). If PAC learning is to be viewed as a universal framework for learning, other forms of learning must then either be shoehorned into this form, declared unimportant, or ignored. Valiant does some of each. Most strikingly, he specifically denies that unsupervised learning (learning from unlabeled examples, as in grouping examples into clusters) is a useful concept in studying natural learning, though he concedes that it may have some value in machine learning. In one case an errant form of learning sneaks in behind Valiant’s back, when he remarks in passing, in a discussion of learning from positive examples, “We may have figured out that each animal belongs to one species.” On the whole, one suspects that the way we figured this out was by learning it, although the problem of learning propositions like “each animal belongs to one species” does not fit well into the framework of supervised learning of categories.\*

本书还包括机器学习和人工智能的展开讨论，尽管机器学习的观点是非常狭隘的。PAC学习很自然地应用于一类相当有限但非常重要的学习问题：从标记数据（“监督”学习）中学习类别，这里有一个精确定义（或至少是相当好的定义）。如果PAC学习被视作一种通用的学习框架，那么其它形式的学习必须被塞进这一形式（宣告不重要）或被忽视。Valiant做了一些工作。最引人注目的是，尽管他承认无监督学习在机器学习中可能有一定的价值，但他特别否认它（从未标记示例中学习，就像将示例分组到聚类中）是研究自然学习的一个有用概念。Valiant在讨论从正实例中学习时顺带提到，在一种异常的学习形式溜到他身后时，“我们或许已经知道了每种动物都属于一个物种”。总的来说，人们推测我们通过学习来弄清楚，尽管像“每种动物都属于一个物种”这样的学习命题问题并不太适合类别的监督学习框架。\*

PAC learning is only one of many general frameworks that have been proposed for learning, and in many ways, it is one of the most limited. Other frameworks include Bayesian learning, minimum description length learning, the Vapnik–Chervonenkis theory of learning, and classical frequentist statistics. V–C theory is mentioned in an endnote, the others not at all.

PAC学习只是为学习提出的众多框架中的一种，在许多方面，它也是最有限的。其他框架包括贝叶斯学习，最小描述长度学习，Vapnik–Chervonenkis学习理论以及经典频率学派统计。V–C理论是在尾注中提到，其它在该书中没有提及。

PAC learning is an elegant and useful approach to a specific class of learning problems. I am doubtful that an approach of this kind is useful in characterizing evolution; it is certainly not a universal framework applicable to all forms of either natural or machine learning.

PAC学习是针对特定学习问题提出的一种优美而有用的方法。我对这种方法是否有助于表征进化持怀疑态度；它可能不是适用于所有自然或机器学习形式的通用框架。

---

\* An observer in a state of nature does not directly perceive species; he perceives animals, their features, and their behaviors. Species are a higher-order construct. Learning the proposition “each animal belongs to one species” involves determining that the class of animals is partitioned into categories, that features and behavior of two animals in the same category are generally much more similar than features and behavior of two animals in different categories, and that animals breed only within the same category.

一个自然状态下的观察者不直接感知物种；他感知动物以及它们的特征和行为。物种是一种高级构想。学习“每种动物都属于一个物种”这样的命题涉及确定动物分类，同一类别中两个动物的特征、行为通常比不同类别中两个动物的特征、行为要更相似，并且动物只在同一类别中存在哺乳行为。