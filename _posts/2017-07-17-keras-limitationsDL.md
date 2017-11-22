---
layout: post
title: "Keras Blog: The limitations of deep learning"
author: "李军"
categories: journal
tags: [deep learning, Keras]
image:
  feature: 
  teaser: 
  credit:
  creditlink:
---

By <u>Francois Chollet</u>

Mon 17 July 2017

This post is adapted from Section 2 of Chapter 9 of my book, [Deep Learning with Python](https://github.com/fchollet/deep-learning-with-python-notebooks) (Manning Publications). It is part of a series of two posts on the current limitations of deep learning, and its future.

This post is targeted at people who already have significant experience with deep learning (e.g. people who have read chapters 1 through 8 of the book). We assume a lot of pre-existing knowledge.

--

**Deep learning: the geometric view**

**深度学习：几何观点**

The most surprising thing about deep learning is how simple it is. Ten years ago, no one expected that we would achieve such amazing results on machine perception problems by using simple parametric models trained with gradient descent. Now, it turns out that all you need is sufficiently large parametric models trained with gradient descent on sufficiently many examples. As Feynman once said about the universe, "It's not complicated, it's just a lot of it".

关于深度学习最令人惊奇的事情是它如此简单。十年前，没有人期望到我们通过使用梯度下降方法训练的简单参数模型将在机器感知问题上取得如此惊奇的结果。现在，你需要的只是在充分多的事例上使用梯度下降训练的充分大的参数模型。正如费曼曾言及宇宙：“It's not complicated, it's just a lot of it”。

In deep learning, everything is a vector, i.e. everything is a point in a geometric space. Model inputs (it could be text, images, etc) and targets are first "vectorized", i.e. turned into some initial input vector space and target vector space. Each layer in a deep learning model operates one simple geometric transformation on the data that goes through it. Together, the chain of layers of the model forms one very complex geometric transformation, broken down into a series of simple ones. This complex transformation attempts to maps the input space to the target space, one point at a time. This transformation is parametrized by the weights of the layers, which are iteratively updated based on how well the model is currently performing. A key characteristic of this geometric transformation is that it must be differentiable, which is required in order for us to be able to learn its parameters via gradient descent. Intuitively, this means that the geometric morphing from inputs to outputs must be smooth and continuous—a significant constraint.

在深度学习中，一切都是向量，也就是说一切都只是几何空间中的点。模型输入（可能是文本、图像等等）和目标首先被向量化，也就是转到某些初始输入向量空间和目标向量空间。深度学习模型的每一层在通过它的数据上进行一个简单几何变换。模型层链接起来形成了一个非常复杂的几何变换，它可以拆分成一系列简单变换。这个复杂变换每次逐点将输入空间映射到目标空间。这个变换由层权重进行参数化，并且基于模型当前性能进行迭代更新。这个几何变换的一个关键特征是它必须可微，目的是能够通过梯度下降来学习参数。直观来看，这意味着从输入到输出的几何渐变必须是平滑连续的，这是一个重要的约束。

The whole process of applying this complex geometric transformation to the input data can be visualized in 3D by imagining a person trying to uncrumple a paper ball: the crumpled paper ball is the manifold of the input data that the model starts with. Each movement operated by the person on the paper ball is similar to a simple geometric transformation operated by one layer. The full uncrumpling gesture sequence is the complex transformation of the entire model. Deep learning models are mathematical machines for uncrumpling complicated manifolds of high-dimensional data.

将这个复杂的几何变换运用到输入数据的整个过程都可以在三维空间中可视化。想象一个正试图将纸球恢复平整的人：弄皱的纸球是模型开始时输入数据的流形。在纸球上进行的每个运动与层上进行的简单几何变换是相似的。全部恢复平整动作的序列是整个模型的复杂变换。深度学习模型就是将复杂的高维数据流形恢复平整的数学机器。

That's the magic of deep learning: turning meaning into vectors, into geometric spaces, then incrementally learning complex geometric transformations that map one space to another. All you need are spaces of sufficiently high dimensionality in order to capture the full scope of the relationships found in the original data.

这就是深度学习的神奇之处：将意思转换成向量和几何空间，然后不断学习从一个空间映射到另一个空间的复杂几何变换。你只需要足够高维的空间来获取在原始数据中发现的全部关系。

**The limitations of deep learning**

**深度学习的局限**

The space of applications that can be implemented with this simple strategy is nearly infinite. And yet, many more applications are completely out of reach for current deep learning techniques—even given vast amounts of human-annotated data. Say, for instance, that you could assemble a dataset of hundreds of thousands—even millions—of English language descriptions of the features of a software product, as written by a product manager, as well as the corresponding source code developed by a team of engineers to meet these requirements. Even with this data, you could not train a deep learning model to simply read a product description and generate the appropriate codebase. That's just one example among many. In general, anything that requires reasoning—like programming, or applying the scientific method—long-term planning, and algorithmic-like data manipulation, is out of reach for deep learning models, no matter how much data you throw at them. Even learning a sorting algorithm with a deep neural network is tremendously difficult.

可以使用这种简单策略实现的应用空间近似无限。而且更多的应用是完全超出当前深度学习技术可达范围的，即使已知大量人类标注的数据。比方说你可以收集一个数以几十万到几亿数据的数据集，这些数据包括产品经理所写的软件产品中特征的英语描述，以及工程师团队为了满足这些需求所开发的源代码。即使有了这些数据，你也不能训练一个深度学习模型简单地读取产品描述并生成合适的代码库。这只是其中的一个例子。通常来讲，不论你喂进多少数据，任何需要类推理编程或应用科学方法-长期规划的事情，以及类算法数据操作的事情都超出了深度学习模型范畴。

This is because a deep learning model is "just" a chain of simple, continuous geometric transformations mapping one vector space into another. All it can do is map one data manifold X into another manifold Y, assuming the existence of a learnable continuous transform from X to Y, and the availability of a dense sampling of X:Y to use as training data. So even though a deep learning model can be interpreted as a kind of program, inversely most programs cannot be expressed as deep learning models—for most tasks, either there exists no corresponding practically-sized deep neural network that solves the task, or even if there exists one, it may not be learnable, i.e. the corresponding geometric transform may be far too complex, or there may not be appropriate data available to learn it.

这是因为深度学习模型仅仅只是一系列将一个向量空间映射到另一个向量空间的简单连续的几何变换。假设存在一个从X到Y的可学习的连续变换以及可以进行X:Y的稠密采样用作训练数据，它能做的是将一个数据流形X映射到另一个数据流形Y。所以即使深度学习模型可以被当作一种程序，但是反过来大多数程序并不能表示成深度学习模型，因为对于大多数任务而言，不存在对应的解决该任务的实践规模的深度神经网络，即使存在，它也许也是不可学习的，也就是说，对应的几何变换太过复杂，或者没有合适的数据用于学习。

Scaling up current deep learning techniques by stacking more layers and using more training data can only superficially palliate some of these issues. It will not solve the more fundamental problem that deep learning models are very limited in what they can represent, and that most of the programs that one may wish to learn cannot be expressed as a continuous geometric morphing of a data manifold.

通过堆叠更多层和使用更多训练数据来扩展当前的深度学习技术只能从外表上减轻一些问题。它并不能解决更基本的问题，如深度学习模型对于它们能表征的特征非常局限，人们希望学习的大多数程序并不能表示成数据流形上的一个连续几何渐变。

**The risk of anthropomorphizing machine learning models**

**人格化机器学习模型的风险**

One very real risk with contemporary AI is that of misinterpreting what deep learning models do, and overestimating their abilities. A fundamental feature of the human mind is our "theory of mind", our tendency to project intentions, beliefs and knowledge on the things around us. Drawing a smiley face on a rock suddenly makes it "happy"—in our minds. Applied to deep learning, this means that when we are able to somewhat successfully train a model to generate captions to describe pictures, for instance, we are led to believe that the model "understands" the contents of the pictures, as well as the captions it generates. We then proceed to be very surprised when any slight departure from the sort of images present in the training data causes the model to start generating completely absurd captions.

当前时代人工智能的一个实际风险是错误阐释深度学习模型所做的事情，高度估计它们的能力。人类心智的基本特征是我们的“心智理论”，即我们将意图、信仰和知识投射在周边事物上的趋向。在石头上画一个笑脸会突然使它“高兴”。运用到深度学习中，意味着比方说，当我们能够成功训练模型来产生描述图片的标题时，我们倾向于相信模型理解了图片中的内容，及由它产生的标题。我们继续惊讶于训练数据中图像的微小改变引起模型开始产生完全荒诞的标题。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/keras-caption_fail.jpg)

Failure of a deep learning-based image captioning system.

In particular, this is highlighted by "adversarial examples", which are input samples to a deep learning network that are designed to trick the model into misclassifying them. You are already aware that it is possible to do gradient ascent in input space to generate inputs that maximize the activation of some convnet filter, for instance—this was the basis of the filter visualization technique we introduced in Chapter 5 (Note: of <u>Deep Learning with Python</u>), as well as the Deep Dream algorithm from Chapter 8. Similarly, through gradient ascent, one can slightly modify an image in order to maximize the class prediction for a given class. By taking a picture of a panda and adding to it a "gibbon" gradient, we can get a neural network to classify this panda as a gibbon. This evidences both the brittleness of these models, and the deep difference between the input-to-output mapping that they operate and our own human perception.

特别地，这可以通过“对抗性事例”来强调，这是被设计用来诱使模型错误分类的深度学习模型的输入采样。你已经知道在输入空间进行梯度下降来生成最大化一些卷积网络滤波器激活函数的输入是可能的，这里的滤波器是我们在<u>Deep Learning with Python</u>一书第5章引入的滤波可视化技术以及第8章深梦算法的基础。相似地，人们可以通过梯度上升法略微修改图片来最大化给定类的类别预测。通过取一张熊猫图像，并把“长臂猿”梯度添加到图像中，我们可以得到将熊猫分类成长臂猿的神经网络。这证实了这些模型的脆弱以及它们操作的输入-输出映射和我们人类感知之间的深度差异。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/keras-adversarial_example.jpg)

An adversarial example: imperceptible changes in an image can upend a model's classification of the image.

In short, deep learning models do not have any understanding of their input, at least not in any human sense. Our own understanding of images, sounds, and language, is grounded in our sensorimotor experience as humans—as embodied earthly creatures. Machine learning models have no access to such experiences and thus cannot "understand" their inputs in any human-relatable way. By annotating large numbers of training examples to feed into our models, we get them to learn a geometric transform that maps data to human concepts on this specific set of examples, but this mapping is just a simplistic sketch of the original model in our minds, the one developed from our experience as embodied agents—it is like a dim image in a mirror.

总之，深度学习模型至少在人类意义上并不理解输入。我们对图像、声音和语言的理解根植于我们的感觉运动经验中，这正体现了人类是地球生物。机器学习模型并没有这样的经历，因此不能以人类相关的方式理解输入。通过将大量标注过的训练实例喂进模型，我们可以使得它们学习将数据映射到这个特定实例的人类概念的几何变换，但这个映射也只是我们心智中最初模型的一个简述，一个从我们经验中发展出的代理，就像镜子中m模糊的像。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/keras-ml_model.jpg)

Current machine learning models: like a dim image in a mirror.

As a machine learning practitioner, always be mindful of this, and never fall into the trap of believing that neural networks understand the task they perform—they don't, at least not in a way that would make sense to us. They were trained on a different, far narrower task than the one we wanted to teach them: that of merely mapping training inputs to training targets, point by point. Show them anything that deviates from their training data, and they will break in the most absurd ways.

作为机器学习实践者，我们要记住这些，并从不陷入这样的陷阱，即相信神经网络能够理解它们进行的任务，它们其实并不能理解，至少不能在对我们有意义的方式上理解。它们在不同的非常狭窄的任务上进行训练，而非以一种我们期望教给它们的方式，它们只是逐点将训练输入映射到训练目标上。提供给它们一些偏离训练数据的信息，它们将变得很荒诞。

**Local generalization versus extreme generalization**

**局部泛化 vs 极度泛化**

There just seems to be fundamental differences between the straightforward geometric morphing from input to output that deep learning models do, and the way that humans think and learn. It isn't just the fact that humans learn by themselves from embodied experience instead of being presented with explicit training examples. Aside from the different learning processes, there is a fundamental difference in the nature of the underlying representations.

在深度学习模型采用的从输入到输出的直接几何渐变和人类思考学习的方式之间似乎存在基本不同。人们从具象经验自身中而非给出精确的训练事例来学习，这不只是一个事实。除了不同的学习过程外，在基本表征的本质中还有一个基本不同。

Humans are capable of far more than mapping immediate stimuli to immediate responses, like a deep net, or maybe an insect, would do. They maintain complex, abstract models of their current situation, of themselves, of other people, and can use these models to anticipate different possible futures and perform long-term planning. They are capable of merging together known concepts to represent something they have never experienced before—like picturing a horse wearing jeans, for instance, or imagining what they would do if they won the lottery. This ability to handle hypotheticals, to expand our mental model space far beyond what we can experience directly, in a word, to perform abstraction and reasoning, is arguably the defining characteristic of human cognition. I call it "extreme generalization": an ability to adapt to novel, never experienced before situations, using very little data or even no new data at all.

人们不仅仅能够像深度网络或昆虫那样将即时刺激映射到即时反应。他们能够维持当前状态、自身以及其他人的复杂抽象的模型，能够使用这些模型预料不同的可能未来，进行长期规划。他们能够将已知概念整合来表示一些他们从未经历过的事情，如画一匹穿着牛仔裤的马，如想象假使他们中彩会做什么。处理假设，拓展我们的心智模型远超我们能够直接体验，总之就是进行抽象和推理的能力，可以论证，就是人类认知的典型特征。我称其为“极度泛化”，即一种只使用极少数据甚至完全不使用新数据就能适用于全新的之前从未经历的状态的一种能力。

This stands in sharp contrast with what deep nets do, which I would call "local generalization": the mapping from inputs to outputs performed by deep nets quickly stops making sense if new inputs differ even slightly from what they saw at training time. Consider, for instance, the problem of learning the appropriate launch parameters to get a rocket to land on the moon. If you were to use a deep net for this task, whether training using supervised learning or reinforcement learning, you would need to feed it with thousands or even millions of launch trials, i.e. you would need to expose it to a dense sampling of the input space, in order to learn a reliable mapping from input space to output space. By contrast, humans can use their power of abstraction to come up with physical models—rocket science—and derive an exact solution that will get the rocket on the moon in just one or few trials. Similarly, if you developed a deep net controlling a human body, and wanted it to learn to safely navigate a city without getting hit by cars, the net would have to die many thousands of times in various situations until it could infer that cars and dangerous, and develop appropriate avoidance behaviors. Dropped into a new city, the net would have to relearn most of what it knows. On the other hand, humans are able to learn safe behaviors without having to die even once—again, thanks to their power of abstract modeling of hypothetical situations.

这与深度网络形成了鲜明的对比，我称深度网络中的方式为“局部泛化”，即深度网络进行的从输入到输出的映射，如果新的输入与训练时看到的有略微不同，深度网络将很快失去理智。比如，考虑学习使得火箭能够着陆月球的合适的发射参数问题。如果你使用深度网络，不论训练时使用监督学习或是强化学习，你都需要喂进数以千计甚至百万计的发射试验，也就是说，为了学习一个从输入空间到输出空间的可靠映射，你需要输入空间的稠密采样来揭露。相比而言，人类可以使用抽象能力想出物理模型-火箭科学，并推导出一个只需要一次或几次尝试就能使火箭到达月球的抽象解。相似地，如果你开发了一个控制人体的深度网络，想要它学习安全地城市导航并不被汽车撞击，网络将必须在大量的状态下死亡成千次直到它能够推理出汽车和危险，形成出合适的规避行为。到了一个新的城市，网络必须重新学习。另一方面，由于抽象建模假设状态的能力，人类甚至不必死亡一次就能过学习到安全行为。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/keras-local_vs_extreme_generalization.jpg)

Local generalization vs. extreme generalization.

In short, despite our progress on machine perception, we are still very far from human-level AI: our models can only perform local generalization, adapting to new situations that must stay very close from past data, while human cognition is capable of extreme generalization, quickly adapting to radically novel situations, or planning very for long-term future situations.

总而言之，尽管我们在机器感知上取得了进展，但我们仍离人类级别的人工智能很遥远，我们的模型只能进行即使调整适应新的状态，仍然必须与过去数据非常接近的局部泛化，然而人类认知能够进行极度泛化，可以快速适应全新状态或规划长期的未来状态。

**Take-aways**

**结论**

Here's what you should remember: the only real success of deep learning so far has been the ability to map space X to space Y using a continuous geometric transform, given large amounts of human-annotated data. Doing this well is a game-changer for essentially every industry, but it is still a very long way from human-level AI.

你应该记住，目前深度学习唯一的成功就是给定大量人类标注的数据，能够使用一个连续几何变换将空间X映射到空间Y。这件事本质上对每个行业来说是一场变革，但是这离人类级别的人工智能仍有很长一段路要走。

To lift some of these limitations and start competing with human brains, we need to move away from straightforward input-to-output mappings, and on to reasoning and abstraction. A likely appropriate substrate for abstract modeling of various situations and concepts is that of computer programs. We have said before (Note: in <u>Deep Learning with Python</u>) that machine learning models could be defined as "learnable programs"; currently we can only learn programs that belong to a very narrow and specific subset of all possible programs. But what if we could learn any program, in a modular and reusable way? Let's see in the next post what the road ahead may look like.

为了消除这些局限并开始与人脑竞争，我们需要从直接的输入-输出映射中离开，转到推理和抽象中。对于大量状态和概念的抽象建模，一个可能合适的底层是计算机程序。我们前面在<u>Deep Learning with Python</u>一书中已经说过机器学习模型可以被定义成“可学习程序”；目前我们只能学习那些属于所有可能程序中非常狭窄的特定子集的程序。但是如果我们能够以一种模块化和可重用的方式学习任何程序将如何呢？


You can read the second part here: <u>The future of deep learning</u>.

@fchollet, May 2017