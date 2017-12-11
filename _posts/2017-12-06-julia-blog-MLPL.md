---
layout: post
title: "[Julia blog] On Machine Learning and Programming Languages"
author: "李军"
categories: journal
tags: [julia, machine learning]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

06 Dec 2017

> Any sufficiently complicated machine learning system contains an ad-hoc, informally-specified, bug-ridden, slow implementation of half of a programming language.[^1]

> 任何足够复杂的机器学习系统都包含一个即席的、非正式的、错误的、缓慢的半编程语言实现。

By Mike Innes (Julia Computing), David Barber (UCL), Tim Besard (UGent), James Bradbury (Salesforce Research), Valentin Churavy (MIT), Simon Danisch (MIT), Alan Edelman (MIT), Stefan Karpinski (Julia Computing), Jon Malmaud (MIT), Jarrett Revels (MIT), Viral Shah (Julia Computing), Pontus Stenetorp (UCL) and Deniz Yuret (Koç University)

As programming languages (PL) people, we have watched with great interest as machine learning (ML) has exploded – and with it, the complexity of ML models and the frameworks people are using to build them. State-of-the-art models are increasingly programs, with support for programming constructs like loops and recursion, and this brings out many interesting issues in the tools we use to create them – that is, programming languages.

作为编程语言（PL）的人们，我们非常关注机器学习（ML）的爆炸式发展，并伴随着ML模型的复杂性和人们正在构建的框架。目前最先进的模型越来越多，支持循环和递归等编程结构，这给我们创建它们的工具——即编程语言带来了许多有趣的问题。

While machine learning does not yet have a dedicated language, several efforts are effectively creating hidden new languages underneath a Python API (like TensorFlow) while others are reusing Python as a modelling language (like PyTorch). We’d like to ask – are new ML-tailored languages required, and if so, why? More importantly, what might the ideal ML language of the future look like?

而机器学习还没有一个专门的语言，一些努力是有效地创造新的语言下面隐藏的Python API（如TensorFlow）则是使用Python作为建模语言（如pytorch）。我们想问一下，是否需要新的ML定制语言，如果是，为什么？更重要的是，未来理想ML语言会是什么样子？

**Pig Latin, and Other Hidden Languages**

**故意颠倒英语字母顺序拼凑而成的行话,以及其它隐藏语言**

TensorFlow (TF) and its ilk[^2] are [already programming languages](https://dl.acm.org/citation.cfm?doid=3088525.3088527), albeit limited ones. This may seem surprising given that one uses Python to program TF. However, consider that TF requires you to write Python code to [build an expression tree](https://www.tensorflow.org/programmers_guide/graphs) in its internal language, which it then evaluates.

TensorFlow（TF）和它的同类已经编程语言，尽管是有限的。考虑到使用Python来编程TF，这似乎令人惊讶。但是，考虑到TF要求您编写Python代码，在其内部语言中构建表达式树，然后对其进行求值。

In fact, you can program in “lazy” TensorFlow style in any language. Consider the following JavaScript code, which implements a trivial function (`add`) in this style:

事实上，你可以在任何语言的懒惰”tensorflow风格的程序。考虑下面的JavaScript代码，它以这种方式实现了一个普通的函数（`add`）：

```julia
function add(a,b) {
  return `${a}+${b}`;
}
x = 1; y = 2
z = add('x', 'y') // 'x+y'
eval(z) // 3
x = 4
eval(z) // 6
```

Here we are metaprogramming – writing code that writes code. In this case both the meta-language and the target language are the same (JavaScript) but they could just as well be different languages (as in the C preprocessor for the C language), or we can use a data structure (an [AST](https://en.wikipedia.org/wiki/Abstract_syntax_tree)) instead of a string – the principle is the same. In TensorFlow, Python serves as a meta-language for writing programs in TF’s graph-based language.[^3] If you’re not convinced, consider that TensorFlow’s graph even supports constructs like [variable scoping](https://www.tensorflow.org/programmers_guide/variables) and [control flow](https://www.tensorflow.org/api_docs/python/tf/cond) – but rather than using Python syntax, you manipulate these constructs through an API.

在这里，我们–写代码，写代码编程。在这种情况下，元语言和目标语言都是相同的（JavaScript），但它们也可以是不同的语言（如C语言的C预处理器），或者我们可以使用数据结构（AST）而不是字符串——原理是相同的。在TensorFlow，Python作为一种元语言编写程序的TF的基于图形的语言。如果你不相信，认为TensorFlow的图甚至支持构造变量作用域和控制流–而不是使用Python的语法，你操纵这些结构通过一个API。

TensorFlow and similar tools present themselves as “just libraries”, but they are extremely unusual ones. Most libraries provide a simple set of functions and data structures, not an entirely new programming system and runtime. Why is such a complex approach necessary?

tensorflow和类似的工具，现在为自己“图书馆”，但他们是非常不寻常的。大多数库提供了一组简单的函数和数据结构，而不是一个全新的编程系统和运行时。为什么需要这种复杂的方法？

**Why create a new language?**

**为什么要创造一种新的编程语言呢?**

The core reason for building new languages is simple: ML research has extremely high computational demands, and simplifying the modelling language makes it easier to add domain-specific optimisations and features. Training models requires excellent hardware support, good numerics, low interpreter overhead and multiple kinds of parallelism. Where general-purpose languages like Python struggle to provide these features, TensorFlow can handle them seamlessly.

构建新的语言核心的原因很简单：ML的研究具有很高的计算需求，简化了建模语言，使它更容易添加特定于域的优化和功能。培养模式需要良好的硬件支持，良好的数字、低开销的解释和多种并行。在通用语言如Python斗争提供这些功能，TensorFlow可以处理无缝。

There’s a snag, though. These impressive optimisations rely on simplifying assumptions (ML models won’t be recursive, or need custom gradients, right?), which make it easier to apply optimisations or deploy to small devices. Unfortunately for engineers, model complexity has increased and researchers thoroughly enjoy violating these assumptions. Models now demand conditional branching (ok, easy enough to hack in), loops for recurrence (less easy but possible), and even [recursion over trees](https://arxiv.org/pdf/1503.00075.pdf) (virtually impossible to deal with). In many areas of ML, including [neural networks](https://blog.keras.io/the-future-of-deep-learning.html) and [probabilistic programming](https://eng.uber.com/pyro/), models are becoming increasingly like programs, including ones that reason about other programs (e.g. [program generators](https://arxiv.org/pdf/1705.03633.pdf) and [interpreters](https://arxiv.org/abs/1605.06640)), and with non-differentiable components like Monte Carlo Tree Search. It’s enormously challenging to build runtimes that provide complete flexibility while achieving top performance, but increasingly the most powerful models and groundbreaking results need both.

虽然有一个障碍。这些令人印象深刻的优化，依靠简化的假设（ML模型不会是递归的，或需要自定义渐变，对吗？），使它更容易应用的优化或部署到小型设备。不幸的是，工程师的模型复杂度增加了，研究人员完全喜欢违反这些假设。现在模型要求条件分支（好，很容易侵入），循环用于递归（不太容易，但可能），甚至递归树（几乎不可能处理）。在ML的许多领域，包括神经网络和概率规划，模型正变得越来越像程序，包括其他程序（例如程序生成器和解释器）的原因，以及不可微的组件，如蒙特卡罗树搜索。它的建立运行时提供完全的灵活性，同时实现高性能的巨大的挑战，但越来越多的最强大的模型和结果都需要突破。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/julia-sentimenttreebank.jpg)
Using ML with complex tree-structured data, like the [Stanford Sentiment Treebank](https://nlp.stanford.edu/sentiment/treebank.html), requires differentiable, recursive algorithms.

Another practical downside of this approach, at least in its current incarnations, is the need for meta-programming of the kind discussed above. Building and evaluating expression trees imposes significant additional burdens on both the programmer and the compiler. It becomes tricky to reason about because the code now has two execution times, each with different language semantics, and things like step-through debugging are much harder. This could be resolved by creating a syntactic language for the new runtime, but this means no less than creating a full new programming language. Is this worthwhile when we have popular numerical languages already?

这种方法的另一个实际缺点是，至少在目前的化身中，需要讨论上述类型的元编程。建立和评估表达式树给程序员和编译器带来了额外的负担。原因很难理解，因为代码现在有两个执行时间，每个都有不同的语言语义，像单步调试这样的事情要困难得多。可以通过为新的运行时创建语法语言来解决这个问题，但这并不意味着要创建一个完整的新编程语言。当我们有流行的数字语言时，这是值得的吗？

**Can we just use Python?**

**我们可以只使用Python语言吗?**

As ML models began to need the full power of a programming language, Chainer and others pioneered a [“define-by-run”](https://arxiv.org/pdf/1701.03980.pdf) approach wherein a Python program is itself the model, using runtime automatic differentiation (AD) for derivatives. This is fantastic from a usability standpoint: If you want a recursive model that operates over trees, simply write that down, and let the AD do its magic! The difference in feel is [hard to overstate](https://twitter.com/karpathy/status/868178954032513024?lang=en), and a frictionless approach to playing with novel ideas is invaluable to research.

为ML模型开始需要一个编程语言的全部力量，链和其他人开创了一个“定义”的方法，其中一个Python程序本身的模型，使用运行时自动分化（AD）衍生物。从可用性角度来看，这很好：如果你想要一个在树上操作的递归模型，只需写下来，让广告发挥魔力！感觉差异是很难夸大，和玩新奇的想法无摩擦的方法是非常宝贵的研究。

However, getting Python to scale to ML’s heavy computational demands is far harder than you might expect. A [huge amount of work](https://www.youtube.com/watch?v=DBVLcgq2Eg0) goes into replicating optimisations that fast languages get for free, and the PL boneyard is full of [high-profile](https://arstechnica.com/information-technology/2009/03/google-launches-project-to-boost-python-performance-by-5x/) yet [failed](https://blog.pyston.org/2017/01/31/pyston-0-6-1-released-and-future-plans/) efforts to make Python faster. [Python’s semantics](http://blog.kevmod.com/2017/02/personal-thoughts-about-pystons-outcome/) also make it fundamentally difficult to provide model-level parallelism or compile models for small devices.

然而，将Python扩展到ML的大量计算需求远比您想象的要困难得多。大量的工作去复制优化，免费获得快速的语言，和PL的坟场是高调却努力使Python更快。Python的语义也使得它很难为小型设备提供模型级并行或编译模型。

Efforts like [Gluon](https://mxnet.incubator.apache.org/api/python/gluon.html) for MXNet are finding ways to get the best of both, at least to some extent. The idea is to combine basic dynamic AD with code-tracing approaches that produce “static sub-graphs” that can be optimised. This is unfortunately something of a mashing together of disparate implementations and APIs. It’s also limited; MXNet uses its graph not just for kernel-level optimisations but also for high-level graph scheduling, such as [splitting a model across multiple GPUs](https://mxnet.incubator.apache.org/how_to/multi_devices.html). It’s unclear how these hybrids will handle this, other than by adding another new API for graph containers whose nodes can be dynamic computations.

努力像胶子为mxnet也在寻找最好的方式，至少在某种程度上。我们的想法是将基本动态广告与跟踪代码的方法结合起来，产生“静态子图”，可以优化。这是一个将不同的实现和API的东西一起。它也是有限的；mxnet利用其图形不只是内核级的优化也为高层次图的调度，如分裂模型在多个GPU。目前还不清楚这些混合动力将如何处理这个问题，而不是为图容器添加另一个新API，它的节点可以是动态计算。

**What might a tailor-made ML language look like?**

**一个特制的ML语言会是什么样子?**

There are few domains as demanding about language-level design issues as machine learning. But it’s not unprecedented, and in areas like [formal reasoning and verification](https://coq.inria.fr) or [cluster computing](https://chapel-lang.org), new, tailor-made languages have proved an effective solution. Similarly, we expect to see new or existing languages customised for the kind of numerical, differentiable, parallelisable and even probabilistic computations needed in ML.

很少有领域像机器学习一样对语言级设计问题提出要求。但这并不是空前的，在诸如形式推理、验证或集群计算等领域，新的、特制的语言被证明是一种有效的解决方案。同样的，我们希望看到新的或现有的语言的数值，可微的定制、可并行的，即使概率的计算需要在ML.

An obvious current challenge for ML languages is achieving generality alongside performance, and the early hybrid approaches will need much more development. We expect that future ML runtimes will need to support arbitrary mixing of approaches (computational graphs that are static within dynamic within static …) and will need to get better at compiling dynamic code for deployment. Ideally, there will only be single, flexible “graph format” (or AST). The AST should have a syntax and statically describe dynamic behaviour (e.g. with a written `for` loop) – in other words, it should look a lot more like a standard programming language.

ML语言目前面临的一个明显挑战是在性能上实现通用性，而早期混合方法需要更多的开发。We expect that future ML runtimes will need to support arbitrary mixing of approaches (computational graphs that are static within dynamic within static …) and will need to get better at compiling dynamic code for deployment. 理想情况下，只有单一的、灵活的“图形格式”（或AST）。AST应该有一个语法和静态描述动态行为（例如用for循环编写）——换句话说，它应该看起来更像一个标准的编程语言。

Programmable semantics would open up new levels of flexibility, and could be provided by a feature similar to macros. This would allow features like multi-GPU training to be built on top of the core system, by specifying where the code should have pure dataflow semantics (as opposed to standard imperative semantics, which are more flexible but may include side-effects that are unsafe to optimise). It could also allow the kinds of program manipulation needed by probabilistic programming languages, or the [vectorisation](https://www.cs.cmu.edu/~guyb/papers/Ble90.pdf) (batching) passes usually implemented by hand in NLP models.

可编程语义将打开新的灵活性级别，并且可以由类似于宏的特性提供。这将允许像多GPU培训这样的特性建立在核心系统的顶部，通过指定代码应该有纯数据流语义（与标准命令语义相反，后者更灵活，但可能包括不安全的副作用）。它也允许程序操作的概率编程语言所需要的类，或向量化（配料）通过通常通过NLP模型。

As well as the PL community, ML engineers should pay close attention to the traditional Automatic Differentiation (AD) community. ML languages can take inspiration from pioneering work on [languages designed for truly first-class derivative](https://arxiv.org/pdf/1611.03416.pdf) support. Such languages can easily mix symbolic with runtime techniques (helping with the tradeoffs mentioned above), mix forward and reverse mode AD (for improved performance and memory usage), and [differentiate GPU kernels](http://mikeinnes.github.io/2017/08/24/cudanative.html) – all with no loss in performance.

除了PL社区外，ML工程师也应该密切关注传统的自动区分（ad）社区。ML语言可以从为真正一流的派生支持设计的语言的开创性工作中获得灵感。这种语言可以很容易地混合符号与运行时技术（帮助上述的权衡），混合正向和反向模式AD（提高性能和内存使用），并区分GPU内核-所有在性能上没有损失。

ML research will increasingly need more powerful type systems, user-defined types and more means for extension. Gone are the days when it was enough to hard-code support for strided arrays on NVIDIA GPUs; cutting-edge techniques like [sparse machine learning](https://people.eecs.berkeley.edu/~elghaoui/Pubs/cidu2011_final.pdf), new hardware like [TPUs](https://cloud.google.com/tpu/), [Nervana](https://www.intelnervana.com) and [FPGAs](https://www.forbes.com/forbes/welcome/?toURL=https://www.forbes.com/sites/moorinsights/2017/08/28/microsoft-fpga-wins-versus-google-tpus-for-ai/&refURL=&referrer=#118733643904), and diverse deployment targets like [ARM chips](http://www.wired.co.uk/article/google-raspberry-pi-ai) or the [iPhone’s CoreML](https://developer.apple.com/documentation/coreml) chip all call for greater levels of flexibility. [Large-scale refactoring of core C++ code](https://github.com/tensorflow/tensorflow/pull/5267/files) for each new development will not scale.

ML研究将越来越需要更强大的类型系统、用户定义类型和扩展的更多手段。飘的日子时，它足以为跨阵列的NVIDIA GPU硬编码的支持；先进的技术如稀疏的机器学习，新的硬件，像TPUs，Nervana和FPGA，多样的部署目标像ARM芯片或iPhone的coreml芯片都需要更高水平的灵活性。大规模的重构核心C++代码的每个新的发展不会规模。

Consider a world where adding new hardware support – or new kinds of data representations – could easily be accomplished by a user in high-level code, without changes to the original system. Here we expect ML systems to take inspiration from existing numerical computing languages, which can [already handle these tasks](https://arxiv.org/pdf/1604.03410.pdf) with ease.

考虑一个世界，在不改变原系统的情况下，可以在高级代码中轻松地添加新的硬件支持（或新的数据表示）。在这里，我们希望ML系统能够从现有的数值计算语言中获得灵感，这些语言可以轻松地处理这些任务。

Type systems can also have safety benefits, but current ones are not suited to array-heavy code where array dimensions are meaningful (for example, spatial vs channel vs batch dimensions in images). These distinctions are left to [pure convention](https://github.com/pytorch/pytorch/issues/1220), and hairy dimension-permuting code has no protection from mistakes, leaving much room for more array-aware type systems. We expect the trend towards dynamic typing to continue,[^4] mainly due to practitioners’ preference for interactivity and scripting, but hope to see further innovations like [CNTK’s optionally dynamic dimensions](https://cntk.ai/pythondocs/sequence.html).

类型系统也可以有安全的好处，但是当前的系统不适合数组尺寸有意义的重代码（例如，空间vs通道与图像中的批处理尺寸）。这些区别是左纯公约和毛维排列代码有错误没有保护，留下更多的阵列感知型系统的房间。我们预计的趋势，动态类型的继续，主要原因在于4者的互动性和脚本的偏好，但希望看到进一步的创新像CNTK的可选的动态尺寸。

ML engineers are increasingly interested in traditional [software engineering problems](https://papers.nips.cc/paper/5656-hidden-technical-debt-in-machine-learning-systems.pdf) like the maintenance and extension of production systems. The [ML programming model](https://medium.com/@karpathy/software-2-0-a64152b37c35) makes it harder to create abstraction barriers and interfaces between components, and re-training of a model can easily break backwards compatibility. ML languages will likely be able to incorporate solutions to these problems just as regular languages do, but this remains an open design problem.

ML工程师越来越感兴趣的传统软件工程问题，如维护和扩展生产系统。ML编程模型很难在组件之间创建抽象的障碍和接口，而对模型的重新训练很容易破坏向后兼容性。ML语言很可能像常规语言一样能够集成这些问题的解决方案，但这仍然是一个开放的设计问题。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/julia-machine_learning_2x.jpg)
Software Engineering 2.0? (via XKCD)

A downside to any new language is that it require a new library ecosystem, as only code written for the new runtime benefits from it. For example, rather than reusing the Python ecosystem, the TensorFlow developers need to rewrite libraries for tasks like [image processing](https://www.tensorflow.org/api_guides/python/image) and [file IO](https://www.tensorflow.org/api_docs/python/tf/TextLineReader) in the graph language, throwing out the vast effort behind projects like SciPy. This may well be the only way forward, but ML practitioners should not split from the wider numerical and HPC community. An ideal ML ecosystem is an ideal numerical one, and vice versa, and collaboration between these communities will multiply everyone’s efforts.

任何新语言的缺点是它需要一个新的库生态系统，因为只有为新运行时编写的代码才能从中受益。例如，而不是使用Python的生态系统，tensorflow开发者需要重写任务，像图中的语言图像处理和文件IO库，把项目像SciPy背后庞大的努力。这可能是唯一的出路，但ML从业者不应该从更广泛的数值和HPC社区分裂。一个理想的ML生态系统是一个理想的数值模型，反之亦然，这些社区之间的协作将使每个人的努力倍增。

We expect to see these developments coming from several angles. Graph IRs and formats like [XLA](https://www.tensorflow.org/performance/xla/), [ONNX](https://github.com/onnx/onnx) and [NNVM](https://github.com/dmlc/nnvm) are becoming ever more sophisticated and will likely take more inspiration from traditional language design,[^5] perhaps even adding surface syntax to become fully-fledged programming languages. TensorFlow’s XLA has started a push towards special-purpose compiler stacks that now includes [TVM](http://tvmlang.org), [DLVM](http://dlvm.org), [myelin](https://github.com/google/sling/tree/master/myelin), and other ongoing work. Meanwhile, projects like the [PyTorch JIT](https://github.com/pytorch/pytorch/tree/master/torch/csrc/jit), [Gluon](https://mxnet.incubator.apache.org/api/python/gluon.html) and [Tangent](https://github.com/google/tangent) are efforts to make Python itself a better modelling language, in spite of the significant challenges. Having just argued that ML is a numerical programming languages problem, we in the Julia community feel that it is an excellent substrate for experimenting with these kinds of language-level issues, and will continue to push the boundaries with projects like [Knet](https://github.com/denizyuret/Knet.jl), [Flux](https://fluxml.github.io), [Cassette](https://github.com/jrevels/Cassette.jl), [CUDAnative](https://github.com/JuliaGPU/CUDAnative.jl), [DataFlow.jl](https://github.com/MikeInnes/DataFlow.jl), and more.

我们期望从几个角度来看待这些事态发展。图IRS和格式如XLA，onnx和nnvm变得越来越复杂，可能会从传统的语言设计以更多的启示，5甚至添加表面语法成为完全成熟的编程语言。tensorflow的XLA已开始向专用编译器栈现在包括TVM，数字地价模型，髓鞘一推，和其他正在进行的工作。同时，项目的pytorch JIT，胶子和切线是努力使Python本身更好的建模语言，尽管在重大的挑战。刚刚认为ML是一种数值编程语言的问题，我们在朱丽亚社区觉得这是尝试用这些语言层面的问题，一个优秀的基板，并将继续与项目如Knet、通量、磁带、cudanative，dataflow.jl推动界限，和更多。

**Conclusion: An Inference about Machine Learning**

**结论：机器学习的推论**

Machine learning models have become extremely general information-processing systems that build ever higher-level and more complex abstractions; recurrence, recursion, higher-order models, even [stack machines](https://nlp.stanford.edu/blog/hybrid-tree-sequence-neural-networks-with-spinn/) and [language interpreters](https://arxiv.org/abs/1605.06640), all implemented as compositions of basic components. ML is a new programming paradigm, albeit a strange one that’s heavily numerical, differentiable and parallel. And as in any engineering field, the tooling available will have a profound impact on the scope and quality of future work.

机器学习模型已经成为非常普遍的信息处理系统，建立更高层次和更复杂的抽象；递归、递归、高阶模型，甚至堆栈机和语言解释器，都是作为基本组件的组成部分来实现的。ML是一种新的编程范式，尽管它是一种奇怪的数值模型，它具有大量的数值性、可微性和并行性。和任何工程领域一样，现有的工具将对未来工作的范围和质量产生深远的影响。

All this suggests that designers of ML systems have a momentous challenge ahead of them. But while that’s true, there’s some good news: The very same problems have been deeply explored, if not already solved, by language researchers over the last few decades! To really take this new field to its full potential, the machine learning and programming languages communities will have to combine forces, and the real challenge is to integrating the disparate expertise of these two groups.

所有这些都表明，ML系统的设计者面临着重大的挑战。但尽管如此，还是有一些好消息：过去几十年中，语言研究者们已经深入探讨了同样的问题，如果不是已经解决的话！要真正发挥这一新领域的全部潜力，机器学习和编程语言社区必须联合力量，真正的挑战是整合这两个群体的不同专业知识。

Can we build systems that treat numerics, derivatives and parallelism as first-class features, without sacrificing traditional programming ideas and wisdom? This is the foundational question which languages over the coming decade will have to answer.

我们可以建立系统，把数字、衍生物和并行性，一流的功能，在不牺牲传统的编程思想和智慧吗？这是未来十年语言必须回答的基本问题。

[^1]: After [Philip Greenspun](https://en.wikipedia.org/wiki/Greenspun%27s_tenth_rule)

[^2]: We use TensorFlow for example, but could substitute other “define-before-run” frameworks like CNTK or MXNet.

[^3]: TensorFlow’s graph is effectively a dataflow-based AST (Abstract Syntax Tree).

[^4]: Though we note that, internally, current systems span the gamut from fully dynamic (PyTorch and its ATen backend) to unusually static (TensorFlow’s XLA and MXNet, where all dimensions are known before the graph is run).

[^5]: Google Brain’s increasing hiring of programming languages experts, such as [Chris Lattner](https://techcrunch.com/2017/08/14/swift-creator-chris-lattner-joins-google-brain-after-tesla-autopilot-stint/), is an interesting development on this point.

