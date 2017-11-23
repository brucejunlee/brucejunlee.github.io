---
layout: post
title: "[SIAM NEWS] Julia: A Fast Language for Numerical Computing"
author: "李军"
categories: journal
tags: [siam, julia]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

By <u>Alan Edelman</u>

March 01, 2016

[Alan Edelman is a professor of applied mathematics at Massachusetts Institute of Technology. He has been working in the area of high performance computing systems, networks, software, and algorithms for 30 years and has won many prizes for his work including the prestigious Gordan Bell Prize, a Householder Prize, and a Babbage Prize. With Julia he sees a fresh approach to high performance technical computing.]

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-julia-1.jpg)

Figure 1. Julia is being used in the development and specification of the next-generation aircraft collision avoidance system.

The Environmental Protection Agency’s discovery that Volkswagen installed emissions-cheating software in over 11 million vehicles last September garnered much attention. According to reports, the software made it seem like the vehicles were releasing significantly less nitrogen oxides than in reality, allowing them to discharge up to 40 times the allowable amount of smog-producing pollution. This prompted The New York Times to call for an openness in software that goes beyond the scientific need for transparency. Software openness is becoming a matter of safety and accountability for compliance purposes. This need applies to more than just cars, as the Internet of Things requires communication of data and instructions among multitudes of devices. Open source is not just a checkbox; easy-to-read common code is increasingly becoming paramount.

美国环境保护署发现，大众公司排放的作弊软件在超过1100万辆，去年九月得到太多的关注。据报道，该软件使车辆看起来释放的氮氧化物比实际排放的要少，使它们排放的烟雾排放量达到40倍。这促使纽约时报呼吁开放软件，这超越了对透明度的科学需求。软件开放正在成为遵守规定的安全和责任的问题。这种需求不仅仅适用于汽车，因为物联网需要大量设备之间的数据和指令的通信。开源不仅仅是一个复选框，易于阅读的公共代码正变得越来越重要。

With its speed, openness, and transparency, Julia is emerging as that “must-have” easy-to-read common language. And in terms of safety and accountability, Julia is being used as the specification language for the next-generation airplane collision avoiding system (see Figure 1).

凭借其速度、开放性和透明度，朱丽亚正在成为“必须具备”易于阅读的通用语言。在安全性和责任性方面，朱丽亚正在被用作下一代飞机防撞系统的规范语言（见图1）。

Why use Julia over languages such as R or Python? The differences lie in the programs’ intricacies. These are all very good languages, but when programming in R or Python the two-language problem  lurks: the need to prototype with one slow dynamic language and rewrite with a fast static language to obtain the final product. Having been around longer than Julia, R and Python have naturally established the kind of popularity that takes some years to acquire. Nevertheless, the two-language problem is very serious. Prototyping in R or Python necessitates a rewrite for speed and deployment. If emissions software is written in Python, one must quickly drill down to C code to understand the details of what is happening. Julia’s advantage is that it solves the two-language problem.

为什么要使用朱丽亚而不是R或Python这样的语言呢？不同之处在于程序的复杂性。这些都是非常好的语言，但当在R或Python编程时，两种语言问题潜伏着：需要用一种缓慢的动态语言进行原型，并用一种快速静态语言重写以获得最终产品。R和Python的时间比朱丽亚长，自然建立了一种需要数年才能获得的声望。然而，这两种语言的问题是非常严重的。R或Python中的原型化需要重写速度和部署。如果排放软件是用Python编写的，你必须迅速钻到C代码去了解正在发生的事情的细节。朱丽亚的优势在于它解决了两个语言问题。

While exact usage statistics are difficult to generate, Julia’s popularity is doubling every nine months, Moore’s law style. There are currently an estimated 100,000 Julia users, nearly 1,000 Julia packages, and more than 400 GitHub contributors. Dozens of universities are also using Julia in classes in engineering, big data, optimization, and numerical analysis, as well as in undergraduate computer science, linear algebra, and statistics. Anecdotally, many engineering and financial companies are using Julia at the “grassroots” level.

虽然精确的使用统计数据很难产生，但朱丽亚的普及率每九个月翻一番，穆尔的法律风格。目前有大约100000Julia用户，近1000朱丽亚包，和超过400的GitHub的贡献。几十所大学也在工程、大数据、最优化、数值分析以及本科生计算机科学、线性代数和统计学等课程中使用朱丽亚。有趣的是，许多工程和金融公司使用的是朱丽亚在“草根”水平。

Nick Trefethen, former SIAM President and my Ph.D. advisor, first got me thinking about how to best articulate Julia’s speed and advantages. I spoke about Julia at the “New Directions in Numerical Computation” linear algebra conference in honor of Trefethen’s 60th birthday this past August. The following commentary includes a few key points from that talk.

Nick Trefethen，暹罗前总统和我的博士导师，让我开始思考如何最好地表达朱丽亚的速度优势。我谈到了朱丽亚在“数值计算”在特雷费森的第六十岁生日刚刚过去的8月荣誉线性代数会议的新方向。下面的评论包括了谈话中的几个要点。

**Placing Emphasis on Performance**

**注重性能**

Julia demonstrates that if designed correctly, the very features that help the computer can also appeal to the human. Those unfamiliar with the transformations of code tend to replace complete understandings with magic accelerators based on some partial truths. Users hear that compiling makes code run faster. Jitting makes code run faster. Vectorizing makes code run faster. Declaring types makes code run faster. 

Julia证明，如果设计正确，帮助计算机的特性也能吸引人类。那些不熟悉代码转换的人倾向于基于一些部分真理来取代对魔术加速器的完全理解。用户听说编译使代码运行得更快。JITting使代码运行得更快。矢量化使代码运行得更快。声明类型使代码运行更快。

Interestingly, what makes an algorithm run faster seems less mysterious than what makes code run fast. Algorithms run quickly when they do not waste time computing unnecessary things. This efficiency can mean taking advantage of structure (as in not multiplying by or adding zeros in sparse matrix computations), or computing only as many digits as are necessary (in iterative methods, or by truncating to take advantage of hardware).

有趣的是，使算法运行得更快的原因似乎比代码运行速度快得多。当他们不浪费时间计算不必要的东西时，算法运行得很快。这种效率意味着可以利用结构（如不乘或添加稀疏矩阵计算零点），或只计算多位数是必要的（在迭代方法，或通过截断利用硬件）。

Ultimately, code runs faster when it is not beleaguered by unnecessary computational baggage. That the computer language is thought of separately from the computer algorithm is unfortunate. When considering numerical error, every computation must work just right. If not, the entire computation goes wrong. The same can be said of performance; a language must be designed just right for speed.

最终，当不被不必要的计算负担困扰时，代码运行得更快。计算机语言被认为与计算机算法分开是不幸的。在考虑数值误差时，每一个计算都必须正确工作。否则，整个计算就出错了。同样的情况也可以说是性能；一种语言的设计必须适合于速度。

The earliest computer languages were designed primarily to meet the needs of the computer, and were close enough to the hardware to be relatively fast. Then came interpreted languages, which were designed primarily to meet the needs of the human. This facilitated productivity and was thus the better choice for most people. Julia finds a new place by striking a reasonable balance between human and computer.

最早的计算机语言主要是为了满足计算机的需要而设计的，而且离硬件比较近，速度相对较快。接着出现了解释性语言，这些语言主要是为了满足人类的需要而设计的。这促进了生产力，因此对大多数人来说是更好的选择。朱丽亚在人与计算机之间找到了合理的平衡，找到了一个新的地方。

People initially thought, almost by some kind of conservation law of nature, that a dynamic mathematical language was required to be slow. Julia shows that a carefully designed language that is comfortable for the programmer can still run quickly. It is important to understand that to date, many interpreted computer languages were designed with use cases in mind, while performance and acceleration came grafted in as potential “add-ons.” Placing more emphasis on performance enhances the cooperation between human and computer.

人们最初认为，几乎是某种自然守恒定律，要求动态的数学语言是缓慢的。朱丽亚表明，一种精心设计的语言对于程序员来说是舒适的，它仍然可以快速运行。重要的是要理解，到目前为止，许多解释性的计算机语言都是用用例设计的，而性能和加速作为潜在的“附加组件”被嫁接起来，更加注重性能提高了人与计算机之间的协作。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-julia-2.jpg)

Figure 2. Julia's implementation of the famous Batman curve. TeX symbols such as \sigma + display beautifully.

**A First Julia Experience: the Batman Curve**

**Julia首次体验:蝙蝠侠曲线**

The famous Batman curve is pictured in Figure 2, which users can experiment with on juliabox.org. The expressions in Figure 2 are equivalent to others that may be found online; I believe this version is much easier for people to read (See interactive code in Lecture 1).

著名的蝙蝠侠曲线如图2所示，用户可以在juliabox.org实验。图2中的表达式相当于在线上可以找到的表达式；我相信这个版本对人们来说更容易阅读（参见第1课的交互式代码）。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-julia-3.jpg)

Figure 3. Julia users rarely look at assembly, but they readily can. Julia’s tight assembly is a clue as to why it is so fast.

**Julia is fast and flexible**

**Julia快速灵活**

Computer programs run faster when they transform to a tight set consisting of a small number of quick execution steps. Consider some uses of the plus character “+.” We ask so very much from plus, and know which plus we mean by context. Assembly language may use different instructions to express the various additions on a machine. The good news is that aside from some pushing, popping, and moving, one can see how tight Julia’s instructions are (see Figure 3).

计算机程序在将它们转换成由少量快速执行步骤组成的紧集时运行得更快。考虑一下加字符“+”的一些用法，我们从加号中非常需要，并且知道加上我们指的是上下文。汇编语言可以使用不同的指令来表示机器上的各种添加。好消息是，除了一些推，弹出和移动，人们可以看到朱丽亚的指令有多紧（见图3）。

Of course, “+” can refer to so much more, including dense matrix addition, sparse matrix addition, structured matrix addition, and any type of combination. The point is that Julia produces tight code in all instances.  

当然，“+”可以指的更多，包括稠密矩阵加法、稀疏矩阵加法、结构化矩阵加法和任何类型的组合。关键是朱丽亚在所有实例中都生成严格的代码。

How does Julia do it? For those desiring a quick answer, “multiple dispatch” is the explanation. The Julia language is built on careful principles of type stability that allow for type inference, which enables Julia to perform proper code selection through the multiple dispatch mechanism. Julia reduces the uncertainty in a computation that can waste time.

朱丽亚是怎么做的？对于那些想要迅速回答的人，“多重分派”就是解释。朱丽亚语言建立在类型稳定性的详细原则之上，允许类型推断，这使得朱丽亚可以通过多个调度机制执行适当的代码选择。朱丽亚减少了计算中的不确定性，这会浪费时间。

One can see multiple dispatch in action with the “@which” command in Figure 4, which allows users to drill into Julia code if they wish to see how it implements various “+” symbols. Without the user declaring types, the Julia program knows which “+” is intended and uses the correct assembly code without wasting time.

您可以看到图4中的“@”命令在操作中的多重分派，它允许用户钻入朱丽亚代码中，如果他们想看到它是如何实现各种“+”符号的。如果没有用户声明类型，朱丽亚程序知道哪个“+”是有意的，使用正确的汇编代码而不会浪费时间。

Julia is very much Julia all the way down. (There are bits of other software, and LLVM at the very bottom.) While Julia uses and plays nicely with packages from Python and other computing languages, it does not need to for speed. Even packages such as LAPACK would likely run as fast and could be more flexible if rewritten in Julia. Other numerical languages are front ends to C, C++, or Fortran.

朱丽亚一路上很像朱丽亚。（也有其他软件，位在最底层。LLVM）而朱丽亚使用起到很好的从Python和其他计算机语言的软件包，它不需要速度。即使包如LAPACK可能跑的一样快，可以更灵活，如果改写朱丽亚。其他数值语言前端的C、C++、Fortran。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-julia-4.jpg)

Figure 4. Multiple dispatch in action with the “@which” command.

**Tropical Numbers**

**热带数**

Tropical algebra offers a “x” that distributes over a “+,” but the two symbols can function as arbitrary operations otherwise, as Françoise Tisseur explained at the Householder Symposium XIX[1].

热带代数提供了一个“X”，分布在一个“+”，但这两个符号可以作为任意操作，否则，弗兰ç瓦兹tisseur在户主会议[解释] 1十九。

Here is the famous MAX+PLUS example in Julia:

这里是Julia中著名的（max，+）的例子：

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-julia-5.jpg)

One can then define tropical numbers of all types: 

然后可以定义所有类型的热带数字：

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-julia-6.jpg)

A few more basics allow for general work with tropical numbers:   

更多的基本知识允许热带数字的一般工作：

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-julia-7.jpg)

Notice that now powers work, matrix multiply works, kronecker products work, etc. This demonstrates Julia’s speed. Julia’s abstractions allow the type information to flow directly through unhindered. For example, a user might think there is quite a lot going on upon defining a fancy tropical number type, but the assembly shows that the code is remarkably very tight:

注意现在异能，矩阵乘法，矩阵的Kronecker积等工作，这证明了朱丽亚的速度。朱丽亚的抽象允许类型信息直接通过不受阻碍地流动。例如，用户可能会认为在定义一个漂亮的热带数字类型时有很多事情要做，但是程序集显示代码非常非常紧凑：

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-julia-8.jpg)

Indeed, users can see the “compare” command in the plus and the “add” command in the times.

事实上，用户可以在“加号”和“添加”命令中看到“比较”命令。

**Open Source Research**

**开源研究**

In reality, Julia is fast because the community cares about performance. Because it is an open project, self-described “performance obsessive types” have flocked to the project, thus boosting Julia’s performance. I personally want to see Julia emerge as the language of high performance computing, blurring the distinction between “Silicon Valley”-style big data and artificial intelligence (AI) computations, Wall Street style number crunching, and National Laboratory style scientific computing.

事实上，朱丽亚很快，因为社区关心业绩。因为这是一个开放的项目，自我描述的“表现强迫型”蜂拥到这个项目，从而提高了朱丽亚的表现。我个人希望看到朱丽亚成为高性能计算的语言，模糊了“硅谷”式大数据与人工智能（AI）计算、华尔街风格数字计算和国家实验室式科学计算之间的区别。

Numerical software research enjoys the benefit of its fruits being quite practical. Those with decades of experience in the business know that users have been sharing code development long before GitHub or the use of the term “open source.”  

数值软件研究具有一定的实用性。那些在企业几十年的经验，知道用户已经早在GitHub或术语“开放源代码使用共享发展。”

It has been a pleasure to nurture the Massachusetts Institute of Technology’s component of this worldwide effort and to experience the brilliant contributions from so many first-class researchers. Experience Julia for yourself by searching “Juliacon2015” online and watching the videos, trying juliabox.org, or visiting julialang.org.

很高兴能培养麻省理工学院在这一世界范围内的努力，并从许多一流的研究人员身上获得卓越的贡献。朱丽亚为自己的经验通过搜索“juliacon2015”在线观看视频，在juliabox.org，或访问julialang.org。

**Acknowledgments:** I’d like to dedicate this article to my Ph.D. adviser and former SIAM President, Nick Trefethen, on the occasion of his 60th birthday.