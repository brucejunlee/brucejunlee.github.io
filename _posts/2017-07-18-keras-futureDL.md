---
layout: post
title: "Keras Blog: The future of deep learning"
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

Mon 18 July 2017

This post is adapted from Section 3 of Chapter 9 of my book, [Deep Learning with Python](https://github.com/fchollet/deep-learning-with-python-notebooks) (Manning Publications). It is part of a series of two posts on the current limitations of deep learning, and its future. You can read the first part here: <u>The Limitations of Deep Learning</u>.

--

Given what we know of how deep nets work, of their limitations, and of the current state of the research landscape, can we predict where things are headed in the medium term? Here are some purely personal thoughts. Note that I don't have a crystal ball, so a lot of what I anticipate might fail to become reality. This is a completely speculative post. I am sharing these predictions not because I expect them to be proven completely right in the future, but because they are interesting and actionable in the present.

假设我们了解深度网络如何工作，以及它们的局限性和研究的当前状况，我们能否预测一段时间内事情的走向呢？这里是一些纯粹的个人想法。我并没有水晶球，所以我预测的许多事情也许并不能成真。这是一篇完全推测性的文章。我分享这些预测不是因为我希望它们能够在将来被证明完全正确，而是因为它们非常有趣，目前非常有价值。

At a high-level, the main directions in which I see promise are:

我能够在一个很高层面上看到希望的主要方向是：

* Models closer to general-purpose computer programs, built on top of far richer primitives than our current differentiable layers—this is how we will get to reasoning and abstraction, the fundamental weakness of current models.

* 模型构建在更加丰富的基础上而非我们目前的可微层上，更加接近于通用目的计算机程序-这就是我们需要获知的推理和抽象能力，这也是目前模型的基本弱势。

* New forms of learning that make the above possible—allowing models to move away from just differentiable transforms.

* 使得上面成为可能的新的学习形式-允许模型远离可微变换。

* Models that require less involvement from human engineers—it shouldn't be your job to tune knobs endlessly.

* 很少需要人类工程师参与的模型-无休止地调整按钮不应该是你的工作。

* Greater, systematic reuse of previously learned features and architectures; meta-learning systems based on reusable and modular program subroutines.

* 对之前学到的特征和结构的更好更系统的重用；基于可重用和模块化程序子例程的元学习系统。

Additionally, do note that these considerations are not specific to the sort of supervised learning that has been the bread and butter of deep learning so far—rather, they are applicable to any form of machine learning, including unsupervised, self-supervised, and reinforcement learning. It is not fundamentally important where your labels come from or what your training loop looks like; these different branches of machine learning are just different facets of a same construct.

此外，这些考虑并不特定于监督学习，它们能够应用到机器学习的任何形式中，包括无监督学习，自监督学习和强化学习。你的标签来自于哪里，你的训练循环看起来像什么都不重要；这些不同的机器学习分支只是同一个结构体的不同面。

Let's dive in.

**Models as programs**

**模型即程序**

As we noted in our previous post, a necessary transformational development that we can expect in the field of machine learning is a move away from models that perform purely pattern recognition and can only achieve local generalization, towards models capable of abstraction and reasoning, that can achieve extreme generalization. Current AI programs that are capable of basic forms of reasoning are all hard-coded by human programmers: for instance, software that relies on search algorithms, graph manipulation, formal logic. In DeepMind's AlphaGo, for example, most of the "intelligence" on display is designed and hard-coded by expert programmers (e.g. Monte-Carlo tree search); learning from data only happens in specialized submodules (value networks and policy networks). But in the future, such AI systems may well be fully learned, with no human involvement.

正如我们在前一篇文章中所提到的，我们在机器学习领域期望的一个必要的变化就是要远离进行纯模式识别，只能实现局部泛化的模型，转向能够实现极度泛化的抽象推理模型。目前能够满足基本推理形式的人工智能程序都是由人类程序员硬编码实现的，如那些依赖搜索算法、图操作和形式逻辑的软件。举一个例子，在DeepMind公司下的AlphaGo中，大多数展示出的“智能”都是由专家程序员设计和硬编码实现的（如蒙特卡洛树搜索）；从数据中学习只发生在特定子模块中（价值网络和策略网络）。但未来这样的人工智能系统也许能够在没有人类参与的情况下完全被学习。

What could be the path to make this happen? Consider a well-known type of network: RNNs. Importantly, RNNs have slightly less limitations than feedforward networks. That is because RNNs are a bit more than a mere geometric transformation: they are geometric transformations repeatedly applied inside a for loop. The temporal for loop is itself hard-coded by human developers: it is a built-in assumption of the network. Naturally, RNNs are still extremely limited in what they can represent, primarily because each step they perform is still just a differentiable geometric transformation, and the way they carry information from step to step is via points in a continuous geometric space (state vectors). Now, imagine neural networks that would be "augmented" in a similar way with programming primitives such as for loops—but not just a single hard-coded for loop with a hard-coded geometric memory, rather, a large set of programming primitives that the model would be free to manipulate to expand its processing function, such as if branches, while statements, variable creation, disk storage for long-term memory, sorting operators, advanced datastructures like lists, graphs, and hashtables, and many more. The space of programs that such a network could represent would be far broader than what can be represented with current deep learning models, and some of these programs could achieve superior generalization power.

路在何方？考虑一类著名的网络：循环神经网络（Recurrent Neural Networks，RNNs）。重要的是，循环神经网络的限制要比前馈网络略微少一些。那是因为循环神经网络不但是区区的几何变换：它们是重复应用在循环内的几何变换。循环的时间由人类开发者硬编码：它是网络的一个内置假设。很自然地，循环神经网络仍然极其局限于它们所能表征的事物，这主要是因为它们进行的每一步仍然只是一个可微的几何变换，它们逐步传送信息的方式也只是通过连续几何空间中的点（即状态向量）。现在，想象这样一个神经网络，它以与for循环等编程原语相似的方式进行增强，但不只是一个简单的带有硬编码几何内存的硬编码for循环，而是大量的编程原语集合，在这样的集合上模型能够自由操作扩展它的处理功能，如if分支，while语句，新建变量，长期内存的磁盘存储，排序算符，如列表、图、散列表等高级数据结构等等。这样的网络能够表示的程序空间将比目前深度学习模型能够表示的宽广的多，这样的一些程序能够实现更好的泛化能力。

In a word, we will move away from having on one hand "hard-coded algorithmic intelligence" (handcrafted software) and on the other hand "learned geometric intelligence" (deep learning). We will have instead a blend of formal algorithmic modules that provide reasoning and abstraction capabilities, and geometric modules that provide informal intuition and pattern recognition capabilities. The whole system would be learned with little or no human involvement.

总之，我们将远离那种一方面拥有“硬编码算法智能”（手工制作的软件），另一方面拥有“可学习几何智能”（深度学习）的境况。代替地，我们将提供推理抽象能力的形式算法模块和提供非正式直觉以及模式识别能力的几何模块融合在一起。整个系统能够在很少甚至没有人类参与的情况下进行学习。

A related subfield of AI that I think may be about to take off in a big way is that of program synthesis, in particular neural program synthesis. Program synthesis consists in automatically generating simple programs, by using a search algorithm (possibly genetic search, as in genetic programming) to explore a large space of possible programs. The search stops when a program is found that matches the required specifications, often provided as a set of input-output pairs. As you can see, is it highly reminiscent of machine learning: given "training data" provided as input-output pairs, we find a "program" that matches inputs to outputs and can generalize to new inputs. The difference is that instead of learning parameter values in a hard-coded program (a neural network), we generate source code via a discrete search process.

我认为也许能够成功的一个人工智能相关子领域是程序合成，特别是神经程序合成。程序合成包括通过一个搜索算法（可能是遗传搜索，正如在遗传编程中）自动生成简单程序来探索一个很大空间的可能程序。当发现程序与需求说明相匹配时停止搜索，这经常被作为一系列输入-输出对。诚如所见，这是不是让我们很快想到机器学习：给定“训练数据”作为输入-输出对，我们发现一个匹配输入与输出的“程序”，并能够泛化到新的输入中。这个差异就在于我们通过一个离散搜索过程产生源码而非在一个硬编码程序（神经网络）中学习参数值。

I would definitely expect this subfield to see a wave of renewed interest in the next few years. In particular, I would expect the emergence of a crossover subfield in-between deep learning and program synthesis, where we would not quite be generating programs in a general-purpose language, but rather, where we would be generating neural networks (geometric data processing flows) augmented with a rich set of algorithmic primitives, such as for loops—and many others. This should be far more tractable and useful than directly generating source code, and it would dramatically expand the scope of problems that can be solved with machine learning—the space of programs that we can generate automatically given appropriate training data. A blend of symbolic AI and geometric AI. Contemporary RNNs can be seen as a prehistoric ancestor to such hybrid algorithmic-geometric models.

我非常希望这个子领域能够在接下来几年内引起一波兴趣。我特别希望在深度学习和程序合成间的交叉子领域的出现，这样我将不需要使用通用编程语言生成程序，而仅仅只需for循环等丰富的算法原语来生成神经网络（几何数据处理流）这将比直接生成源码更加易于处理和有用，并且将大大扩展可以通过机器学习解决的问题域和可以通过给定合适的训练数据自动生成的程序空间。这是符号人工智能和几何人工智能的融合。目前的循环神经网络可以被视作这样一个混成的算法-几何模型的史前先驱。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/keras-metalearning1.jpg)

A learned program relying on both geometric (pattern recognition, intuition) and algorithmic (reasoning, search, memory) primitives.

Figure: A learned program relying on both geometric primitives (pattern recognition, intuition) and algorithmic primitives (reasoning, search, memory).

**Beyond backpropagation and differentiable layers**

**超越反向传播和可微层**

If machine learning models become more like programs, then they will mostly no longer be differentiable—certainly, these programs will still leverage continuous geometric layers as subroutines, which will be differentiable, but the model as a whole would not be. As a result, using backpropagation to adjust weight values in a fixed, hard-coded network, cannot be the method of choice for training models in the future—at least, it cannot be the whole story. We need to figure out to train non-differentiable systems efficiently. Current approaches include genetic algorithms, "evolution strategies", certain reinforcement learning methods, and ADMM (alternating direction method of multipliers). Naturally, gradient descent is not going anywhere—gradient information will always be useful for optimizing differentiable parametric functions. But our models will certainly become increasingly more ambitious than mere differentiable parametric functions, and thus their automatic development (the "learning" in "machine learning") will require more than backpropagation.

如果机器学习模型变得更加像程序，那么它们将变得不再可微，无疑地是这些程序将仍然使用连续几何层作为子例程，这些子例程是可微的，但是模型作为整体将不再可微。结果，使用反响传播在一个固定的硬编码网络中调整权值将不能作为未来训练模型的一个方法选择，至少它不再是网络的全部。我们需要弄清楚如何高效地训练不可微的系统。目前的方法包括遗传算法，“进化策略”，某些强化学习方法和交替方向乘子算法（alternating direction method of multipliers，ADMM）等。梯度下降自然不再无处不在-梯度信息对于可微参数函数的优化总是非常有用的。但我们的模型无疑将比仅仅可微参数函数更有前景，它们的自动开发（即在“机器学习”中的“学习”）需要的远不止反向传播。

Besides, backpropagation is end-to-end, which is a great thing for learning good chained transformations, but is rather computationally inefficient since it doesn't fully leverage the modularity of deep networks. To make something more efficient, there is one universal recipe: introduce modularity and hierarchy. So we can make backprop itself more efficient by introducing decoupled training modules with some synchronization mechanism between them, organized in a hierarchical fashion. This strategy is somewhat reflected in DeepMind's recent work on "synthetic gradients". I would expect more more work along these lines in the near future.

此外，反向传播是端到端的，这对于学习好的链式变换是一件重要的事情，但从计算上来看是非常低效的，因为它没有完全使用深度网络的模块化。有一种普适的做法来提高效率：引入模块化和层级。我们可以通过引入带有某种同步机制，按层级方式组织的解耦训练模块使得反向传播更高效。这个策略有点反映在最近DeepMind关于“合成梯度”的工作中。我期望在不久的将来有更多关于这些的工作。

One can imagine a future where models that would be globally non-differentiable (but would feature differentiable parts) would be trained—grown—using an efficient search process that would not leverage gradients, while the differentiable parts would be trained even faster by taking advantage of gradients using some more efficient version of backpropagation.

人们可以想象，未来有这样一个全局不可微的模型（但可以刻画可微部分），将使用一个没有梯度的高效搜索过程来不断训练，然而可微部分可以使用某些更高效的反向传播利用梯度优势来更快训练。

**Automated machine learning**

**自动机器学习**

In the future, model architectures will be learned, rather than handcrafted by engineer-artisans. Learning architectures automatically goes hand in hand with the use of richer sets of primitives and program-like machine learning models.

未来模型架构也可以被学习，而非工程师手工制作。自动学习架构将与更加丰富的原语和类似程序的机器学习模型的使用紧密联系。

Currently, most of the job of a deep learning engineer consists in munging data with Python scripts, then lengthily tuning the architecture and hyperparameters of a deep network to get a working model—or even, to get to a state-of-the-art model, if the engineer is so ambitious. Needless to say, that is not an optimal setup. But AI can help there too. Unfortunately, the data munging part is tough to automate, since it often requires domain knowledge as well as a clear high-level understanding of what the engineer wants to achieve. Hyperparameter tuning, however, is a simple search procedure, and we already know what the engineer wants to achieve in this case: it is defined by the loss function of the network being tuned. It is already common practice to set up basic "AutoML" systems that will take care of most of the model knob tuning. I even set up my own years ago to win Kaggle competitions.

目前，深度学习工程师的大部分工作包括使用Python脚本清洗数据，然后长时间调整架构和深度网络的超参数来得到一个工作模型，如果工程师很有志向甚至能获得目前最好的模型。不用说就知道那不是最优设置。但人工智能在这里也能起作用。不幸的是，数据清洗部分很难自动化，因为它经常需要领域知识还有对工程师意图实现功能的高度理解。但超参调整是一个相对简单的搜索过程，我们也已经知道工程师想要实现的方式：它通过将被调整网络的损失函数来定义。建立基本的考虑大多数模型按钮调整的“自动机器学习”系统已成为一种常例。我甚至在数年前就已经建立了自己的系统并赢得了Kaggle竞赛。

At the most basic level, such a system would simply tune the number of layers in a stack, their order, and the number of units or filters in each layer. This is commonly done with libraries such as Hyperopt, which we discussed in Chapter 7 (Note: of <u>Deep Learning with Python</u>). But we can also be far more ambitious, and attempt to learn an appropriate architecture from scratch, with as few constraints as possible. This is possible via reinforcement learning, for instance, or genetic algorithms.

这样的系统将简单地按顺序调整层数和每一层内的单元数或过滤器数。这通过使用Hyperopt（我们在<u>Deep Learning with Python</u>一书第7章中讨论）等库来做。但我们也可以更有志向，设法只需要很少的一些约束从头开始学习一个合适的架构。比方说我们可以通过强化学习或遗传算法来实现。

Another important AutoML direction is to learn model architecture jointly with model weights. Because training a new model from scratch every time we try a slightly different architecture is tremendously inefficient, a truly powerful AutoML system would manage to evolve architectures at the same time as the features of the model are being tuned via backprop on the training data, thus eliminating all computational redundancy. Such approaches are already starting to emerge as I am writing these lines.

另一个重要的自动机器学习方向是联合模型权重来学习模型架构。因为每次我们尝试略微不同的架构时从头开始训练一个新模型是非常低效的，一个真正强大的自动机器学习系统将同时逐步演化架构，模型的特征通过训练数据上的反向传播来调整，因而消除了所有的计算冗余。这样的方法在我正在写这些时已经开始出现了。

When this starts happening, the jobs of machine learning engineers will not disappear—rather, engineers will move higher up the value creation chain. They will start putting a lot more effort into crafting complex loss functions that truly reflect business goals, and understanding deeply how their models impact the digital ecosystems in which they are deployed (e.g. the users that consume the model's predictions and generate the model's training data) —problems that currently only the largest company can afford to consider.

当这些开始发生时，机器学习工程师的工作并不会消失，而是到达更高的价值创造链。他们开始将更多的精力投入到真正能反映业务目标的复杂损失函数的制作中，深入理解他们的模型将如何影响数字生态系统（如使用模型预测以及生成模型训练数据的用户），以及目前只有最大的公司能够考虑的问题。

**Lifelong learning and modular subroutine reuse**

**终身学习和模块化子程序重用**

If models get more complex and are built on top of richer algorithmic primitives, then this increased complexity will require higher reuse between tasks, rather than training a new model from scratch every time we have a new task or a new dataset. Indeed, a lot datasets would not contain enough information to develop a new complex model from scratch, and it will become necessary to leverage information coming from previously encountered datasets. Much like you don't learn English from scratch every time you open a new book—that would be impossible. Besides, training models from scratch on every new task is very inefficient due to the large overlap between the current tasks and previously encountered tasks.

如果模型变得更复杂，并构建在更丰富的算法原语之上，那么这样的复杂性将需要任务之间更高的重用，而非每次我们有一个新任务或新数据集时都从零开始训练新模型。许多数据集的确并不包含足够的信息来从零开始开发一个新的复杂模型，使用来自于之前遇到过的数据集中的信息是必要的。这就像你并不需要每次打开一本新书时就从头开始学习英语，这也是不可能的。而且，由于目前任务和之前遇到的任务间存在很大的重叠，在每个新的任务上从零开始训练模型是非常低效的。

Additionally, a remarkable observation that has been made repeatedly in recent years is that training a same model to do several loosely connected tasks at the same time results in a model that is better at each task. For instance, training a same neural machine translation model to cover both English-to-German translation and French-to-Italian translation will result in a model that is better at each language pair. Training an image classification model jointly with an image segmentation model, sharing the same convolutional base, results in a model that is better at both tasks. And so on. This is fairly intuitive: there is always some information overlap between these seemingly disconnected tasks, and the joint model has thus access to a greater amount of information about each individual task than a model trained on that specific task only.

另外，近年反复出现的一个显著观察是训练一个同时做几个联系不太紧密的任务的相同模型结果会产生一个对每个任务都更优的模型。例如，训练一个覆盖英语-德语翻译和法语-意大利语翻译的相同的神经机器翻译模型将产生一个对每个语言对都更优的模型。联合图像分割模型，训练一个共享相同卷积基的图像分类模型将产生对这两个任务都更优的模型。等等诸如此类。这是相对直观的：在这些貌似不相连的任务间总是有一些信息重叠，因此相对在特定任务上单独训练的模型，联合模型能够获得更多的关于每个任务的信息。

What we currently do along the lines of model reuse across tasks is to leverage pre-trained weights for models that perform common functions, like visual feature extraction. You saw this in action in Chapter 5. In the future, I would expect a generalized version of this to be commonplace: we would not only leverage previously learned features (submodel weights), but also model architectures and training procedures. As models become more like programs, we would start reusing program subroutines, like the functions and classes found in human programming languages.

目前我们沿着跨任务的模型重用这条路上所做的是利用完成相同功能（如视觉特征抽取）的模型的预训练权重。你可以在第5章中看到实践。未来，我将期望一个普适的泛化：我们不仅能够利用之前学到的特征（子模型权重），而且能够建模架构和训练过程。随着模型越来越像程序，我们将开始重用程序子例程，正如在人类编程语言中找到的函数与类。

Think of the process of software development today: once an engineer solves a specific problem (HTTP queries in Python, for instance), they will package it as an abstract and reusable library. Engineers that face a similar problem in the future can simply search for existing libraries, download one and use it in their own project. In a similar way, in the future, meta-learning systems will be able to assemble new programs by sifting through a global library of high-level reusable blocks. When the system would find itself developing similar program subroutines for several different tasks, if would come up with an "abstract", reusable version of the subroutine and would store it in the global library. Such a process would implement the capability for abstraction, a necessary component for achieving "extreme generalization": a subroutine that is found to be useful across different tasks and domains can be said to "abstract" some aspect of problem-solving. This definition of "abstraction" is similar to the notion of abstraction in software engineering. These subroutines could be either geometric (deep learning modules with pre-trained representations) or algorithmic (closer to the libraries that contemporary software engineers manipulate).

考虑一下如今的软件开发过程：一旦工程师解决了一个特定问题（如Python中的HTTP查询），他们将其打包成一个抽象可重用的库。未来面对相似问题的工程师就能够搜索已经存在的库，下载并用在他们自己的项目中。相似地，未来元学习系统也能够通过筛选包含高级可重用块的全局库来装配新的程序。当系统发现自身正在开发几个不同任务的相似程序子例程时，如果能够想出一个“抽象”可重用的子例程并将其存储在全局库中。这样一个过程能够实现抽象能力，这是达到“极度泛化”的一个要素：对于不同任务非常有用的子例程以及能够“抽象”待解问题的某些方面的领域知识。这里“抽象”的定义同软件工程中的抽象概念是相似的。这些子例程要么是几何的（带有预训练表征的深度学习模块），要么是算法的（与当前的软件工程师操纵的库非常相近）。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/keras-metalearning2.jpg)

A meta-learner capable of quickly developing task-specific models using reusable primitives (both algorithmic and geometric), thus achieving "extreme generalization".

Figure: A meta-learner capable of quickly developing task-specific models using reusable primitives (both algorithmic and geometric), thus achieving "extreme generalization".

**In summary: the long-term vision**

**总结: 长期愿景**

In short, here is my long-term vision for machine learning:

总而言之，这里是我对机器学习的长期愿景：

* Models will be more like programs, and will have capabilities that go far beyond the continuous geometric transformations of the input data that we currently work with. These programs will arguably be much closer to the abstract mental models that humans maintain about their surroundings and themselves, and they will be capable of stronger generalization due to their rich algorithmic nature.

* 模型将更像程序，并超越当前我们使用的对输入数据的连续几何变换能力。这些程序可以说更接近于人类维持周边和自身信息的抽象智力模型，由于丰富的算法特性它们能够进行更强泛化。

* In particular, models will blend algorithmic modules providing formal reasoning, search, and abstraction capabilities, with geometric modules providing informal intuition and pattern recognition capabilities. AlphaGo (a system that required a lot of manual software engineering and human-made design decisions) provides an early example of what such a blend between symbolic and geometric AI could look like.

* 特别地，模型混合了形式推理、搜索等算法模块和抽象能力，以及提供非正式直觉和模式识别能力的几何模块。AlphaGo（一款需要人工软件工程和人为的设计决策的系统）提供了符号人工智能和几何人工智能的混合视图的一个早期实例。

* They will be grown automatically rather than handcrafted by human engineers, using modular parts stored in a global library of reusable subroutines—a library evolved by learning high-performing models on thousands of previous tasks and datasets. As common problem-solving patterns are identified by the meta-learning system, they would be turned into a reusable subroutine—much like functions and classes in contemporary software engineering—and added to the global library. This achieves the capability for abstraction.

* 它们将使用存储在可重用子例程的全局库（一个通过在之前数以千计的任务和数据集上学习高性能模型来逐步发展的库）中的模块部分自动成长，而非由人类工程师手动制作。因为通常的问题解决模式是由元学习系统来辨别的，它们将转向一个可重用的子例程（这很像当前软件工程中的函数和类）并将其加进全局库。这就实现了抽象能力。

* This global library and associated model-growing system will be able to achieve some form of human-like "extreme generalization": given a new task, a new situation, the system would be able to assemble a new working model appropriate for the task using very little data, thanks to 1) rich program-like primitives that generalize well and 2) extensive experience with similar tasks. In the same way that humans can learn to play a complex new video game using very little play time because they have experience with many previous games, and because the models derived from this previous experience are abstract and program-like, rather than a basic mapping between stimuli and action.

* 这个全局库和相关的模型成长系统能够实现一些类人的“极度泛化”形式：给定一个新任务，新环境，系统只使用很少的数据就能够形成一个新的适合于该任务的模型，这主要是由于1）泛化很好的丰富的类程序原语；2）全面的相似任务的经验。人只需要很少的体验时间就能学会玩一个新的非常复杂的视频游戏，因为他们已经有了很多之前的游戏经验，并且通过这个经验推导出的模型是抽象的类程序的，而不是刺激和动作之间的一个基本映射。

* As such, this perpetually-learning model-growing system could be interpreted as an AGI—an Artificial General Intelligence. But don't expect any singularitarian robot apocalypse to ensue: that's a pure fantasy, coming from a long series of profound misunderstandings of both intelligence and technology. This critique, however, does not belong here.

* 如此，这个不断成长的永久学习系统能够被解释成通用人工智能。但不要期望任何奇点机器人末日的来临：这完全是来自于长期的智能和技术方面的极大误解而产生的幻想。然而这个评论与该文章无关。

@fchollet, May 2017