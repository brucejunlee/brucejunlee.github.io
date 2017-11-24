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

美国环境保护署去年九月份发现大众在超过1100万辆车上安装了排放检测软件，这一发现得到了很多关注。据报道，该软件使车辆看上去排放的氮氧化物比实际排放的要少，这使得它们实际排放量高达允许烟雾排放量的40倍。这促使纽约时报呼吁开放软件，这超出了对透明度的科学需求。软件开放正在成为遵守规定的安全和责任问题。这一需求不仅仅适用于汽车，因为物联网也需要大量设备之间的数据和指令通信。开源不仅仅是一个复选框，易读的公共代码正变得越来越重要。

With its speed, openness, and transparency, Julia is emerging as that “must-have” easy-to-read common language. And in terms of safety and accountability, Julia is being used as the specification language for the next-generation airplane collision avoiding system (see Figure 1).

凭借其速度、开放性和透明度，Julia正在成为“必须具备的”易读的通用语言。在安全和责任方面，Julia正在被用作下一代飞机防撞系统的规范语言（见图1）。

Why use Julia over languages such as R or Python? The differences lie in the programs’ intricacies. These are all very good languages, but when programming in R or Python the two-language problem  lurks: the need to prototype with one slow dynamic language and rewrite with a fast static language to obtain the final product. Having been around longer than Julia, R and Python have naturally established the kind of popularity that takes some years to acquire. Nevertheless, the two-language problem is very serious. Prototyping in R or Python necessitates a rewrite for speed and deployment. If emissions software is written in Python, one must quickly drill down to C code to understand the details of what is happening. Julia’s advantage is that it solves the two-language problem.

那为什么要使用Julia而不是R或Python这样的语言呢？不同之处在于程序的复杂性。这些都是非常好的语言，但使用R或Python编程时，存在两语言问题：需要用一种缓慢的动态语言构造原型，并用一种快速的静态语言重写以获得最终产品。R和Python比Julia出现的时间早很多，自然就建立了一种需要数年才能获得的声望。然而，两语言问题是非常严重的。R或Python中构建的原型需为了速度和部署需要必须重写。如果尾气排放软件是用Python编写的，你必须迅速钻到C代码中去了解正在发生的细节。Julia的优势在于它解决了两语言问题。

While exact usage statistics are difficult to generate, Julia’s popularity is doubling every nine months, Moore’s law style. There are currently an estimated 100,000 Julia users, nearly 1,000 Julia packages, and more than 400 GitHub contributors. Dozens of universities are also using Julia in classes in engineering, big data, optimization, and numerical analysis, as well as in undergraduate computer science, linear algebra, and statistics. Anecdotally, many engineering and financial companies are using Julia at the “grassroots” level.

虽然精确的使用统计数据很难获得，但Julia的普及率每九个月就翻一番，这是典型的摩尔定律。目前大约有十万位Julia用户，近1000个Julia包和超过400名GitHub贡献者。数十所大学也在工程、大数据、优化、数值分析以及本科计算机科学、线性代数和统计学等课程中使用Julia。有趣的是，许多工程和金融公司也在基层使用Julia。

Nick Trefethen, former SIAM President and my Ph.D. advisor, first got me thinking about how to best articulate Julia’s speed and advantages. I spoke about Julia at the “New Directions in Numerical Computation” linear algebra conference in honor of Trefethen’s 60th birthday this past August. The following commentary includes a few key points from that talk.

Nick Trefethen是SIAM前主席和我的博士导师，他最先让我思考如何最好地表达清楚Julia的速度和优势。为了祝贺去年八月份Trefethen六十岁生日，我在“New Directions in Numerical Computation”线性代数会议上谈到了Julia。下面的评论包括了谈话中的几个要点。

**Placing Emphasis on Performance**

**注重性能**

Julia demonstrates that if designed correctly, the very features that help the computer can also appeal to the human. Those unfamiliar with the transformations of code tend to replace complete understandings with magic accelerators based on some partial truths. Users hear that compiling makes code run faster. Jitting makes code run faster. Vectorizing makes code run faster. Declaring types makes code run faster. 

Julia证明，那些有助于计算机的特性如果正确设计的话对人类也很有吸引力。那些不熟悉代码转换的人倾向于用以某些部分事实为基础的魔术加速器来取代对代码的完全理解。用户知道编译使代码运行得更快，JIT使代码运行得更快。向量化使代码运行得更快以及声明类型使代码运行更快。

Interestingly, what makes an algorithm run faster seems less mysterious than what makes code run fast. Algorithms run quickly when they do not waste time computing unnecessary things. This efficiency can mean taking advantage of structure (as in not multiplying by or adding zeros in sparse matrix computations), or computing only as many digits as are necessary (in iterative methods, or by truncating to take advantage of hardware).

有趣的是，使算法运行得更快似乎比不上使代码运行得更快神秘。当没有浪费时间计算不必要的东西时，算法运行得很快。这种高效性意味着可以利用结构（如在稀疏矩阵计算中不乘零或不加零），或只计算尽可能多的必要数（如在迭代方法中，或通过截断来利用硬件优势）。

Ultimately, code runs faster when it is not beleaguered by unnecessary computational baggage. That the computer language is thought of separately from the computer algorithm is unfortunate. When considering numerical error, every computation must work just right. If not, the entire computation goes wrong. The same can be said of performance; a language must be designed just right for speed.

最终，当不被不必要的计算负担困扰时，代码运行得更快。计算机语言与计算机算法被分开思考是不幸的。在考虑数值误差时，每个计算都必须正确进行。否则，整个计算就出错了。同样的情况也适用于性能；必须设计一款为了速度的语言。

The earliest computer languages were designed primarily to meet the needs of the computer, and were close enough to the hardware to be relatively fast. Then came interpreted languages, which were designed primarily to meet the needs of the human. This facilitated productivity and was thus the better choice for most people. Julia finds a new place by striking a reasonable balance between human and computer.

最早的计算机语言主要是为了满足计算机需要而设计的，而且非常接近硬件，速度相对较快。接着出现了解释性语言，这些语言主要是为了满足人类需要而设计的。这促进了生产力，因此对大多数人来说是更好的选择。而Julia在人与计算机之间找到了合理的平衡。

People initially thought, almost by some kind of conservation law of nature, that a dynamic mathematical language was required to be slow. Julia shows that a carefully designed language that is comfortable for the programmer can still run quickly. It is important to understand that to date, many interpreted computer languages were designed with use cases in mind, while performance and acceleration came grafted in as potential “add-ons.” Placing more emphasis on performance enhances the cooperation between human and computer.

人们最初认为，由于某种自然守恒定律，动态数学语言很慢。Julia表明，一种对程序员来说舒适的精心设计的语言，仍然可以快速运行。重要的是要理解，到目前为止，许多解释性的计算机语言都是用用例设计的，而性能和加速作为潜在的“附件”被嫁接起来，对性能的更多强调提高了人机之间的协作。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-julia-2.jpg)

Figure 2. Julia's implementation of the famous Batman curve. TeX symbols such as \sigma + display beautifully.

**A First Julia Experience: the Batman Curve**

**Julia首次体验:蝙蝠侠曲线**

The famous Batman curve is pictured in Figure 2, which users can experiment with on juliabox.org. The expressions in Figure 2 are equivalent to others that may be found online; I believe this version is much easier for people to read (See interactive code in Lecture 1).

著名的蝙蝠侠曲线如图2所示，用户可以在juliabox.org上实验。图2中的表达式与网上可以找到的其它表达式是等价的；但我认为这个版本更易读（参见Lecture 1 的交互式代码）。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-julia-3.jpg)

Figure 3. Julia users rarely look at assembly, but they readily can. Julia’s tight assembly is a clue as to why it is so fast.

**Julia is fast and flexible**

**Julia快速灵活**

Computer programs run faster when they transform to a tight set consisting of a small number of quick execution steps. Consider some uses of the plus character “+”. We ask so very much from plus, and know which plus we mean by context. Assembly language may use different instructions to express the various additions on a machine. The good news is that aside from some pushing, popping, and moving, one can see how tight Julia’s instructions are (see Figure 3).

当转换成由少量快速执行步骤组成的紧集时计算机程序将运行得更快。考虑一下加号“+”的一些用法，我们使用加号，在上下文环境中知道我们指的是哪一个加号。汇编语言可以使用不同的指令来表示机器上的各种加法。好消息是，除了一些push、pop和move操作外，人们可以看到Julia指令有多紧凑（见图3）。

Of course, “+” can refer to so much more, including dense matrix addition, sparse matrix addition, structured matrix addition, and any type of combination. The point is that Julia produces tight code in all instances.  

当然，“+”可以指的更多，包括稠密矩阵加法、稀疏矩阵加法、结构化矩阵加法和任何类型的组合等等。关键是Julia在所有实例中都能生成紧凑代码。

How does Julia do it? For those desiring a quick answer, “multiple dispatch” is the explanation. The Julia language is built on careful principles of type stability that allow for type inference, which enables Julia to perform proper code selection through the multiple dispatch mechanism. Julia reduces the uncertainty in a computation that can waste time.

Julia是怎么做的呢？对于那些想要快速得到答案的人来说，“多指派”就是解释。Julia语言建立在允许类型推断的类型稳定性原则之上，这使得Julia可以通过多指派机制来进行适当的代码选择。Julia减少了会造成时间浪费的计算中的不确定性。

One can see multiple dispatch in action with the “@which” command in Figure 4, which allows users to drill into Julia code if they wish to see how it implements various “+” symbols. Without the user declaring types, the Julia program knows which “+” is intended and uses the correct assembly code without wasting time.

您可以看到图4中使用“@which”命令来了解实际操作中的多指派，用户可以钻入Julia代码中来看看它是如何实现各种“+”号的。没有用户声明类型，Julia程序也能知道想要哪个“+”，并毫不费时地使用正确的汇编代码。

Julia is very much Julia all the way down. (There are bits of other software, and LLVM at the very bottom.) While Julia uses and plays nicely with packages from Python and other computing languages, it does not need to for speed. Even packages such as LAPACK would likely run as fast and could be more flexible if rewritten in Julia. Other numerical languages are front ends to C, C++, or Fortran.

Julia自始至终都是Julia（也有一些其他软件，底层使用LLVM）。如果不考虑速度，Julia也能很好地使用来自Python和其他计算机语言的软件包。如果用Julia重写，甚至如LAPACK这样的包也可能快速灵活地运行。而其他的数值语言都作为C、C++或Fortran的前端。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-julia-4.jpg)

Figure 4. Multiple dispatch in action with the “@which” command.

**Tropical Numbers**

**热带数**

Tropical algebra offers a “x” that distributes over a “+”, but the two symbols can function as arbitrary operations otherwise, as Françoise Tisseur explained at the Householder Symposium XIX[1].

热带代数提供了一个分布在“+”上的“x”，但这两个符号可以作为任意操作，正如Françoise Tisseur在第19届Householder研讨会上所说。

Here is the famous MAX+PLUS example in Julia:

这里是Julia中著名的（max，+）的例子：

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-julia-5.jpg)

One can then define tropical numbers of all types: 

然后可以定义所有类型的热带数：

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-julia-6.jpg)

A few more basics allow for general work with tropical numbers:   

更多的允许使用热带数的基础知识：

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-julia-7.jpg)

Notice that now powers work, matrix multiply works, kronecker products work, etc. This demonstrates Julia’s speed. Julia’s abstractions allow the type information to flow directly through unhindered. For example, a user might think there is quite a lot going on upon defining a fancy tropical number type, but the assembly shows that the code is remarkably very tight:

注意现在幂乘、矩阵乘法以及矩阵的Kronecker积等都可以，这证明了Julia的速度。Julia的抽象能力使得类型信息能够畅通无阻地直接流过。例如，用户可能会认为在定义一个漂亮的热带数类型时有很多事情要做，但是汇编程序显示代码非常非常紧凑：

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-julia-8.jpg)

Indeed, users can see the “compare” command in the plus and the “add” command in the times.

事实上，用户可以在加中看到“比较”指令，在乘中看到“相加”指令。

**Open Source Research**

**开源研究**

In reality, Julia is fast because the community cares about performance. Because it is an open project, self-described “performance obsessive types” have flocked to the project, thus boosting Julia’s performance. I personally want to see Julia emerge as the language of high performance computing, blurring the distinction between “Silicon Valley”-style big data and artificial intelligence (AI) computations, Wall Street style number crunching, and National Laboratory style scientific computing.

事实上，Julia很快是因为社区非常关心性能表现。因为这是一个开放的项目，自我描述的“性能强迫型”蜂拥到这个项目中，从而提升了Julia的性能。我个人希望看到Julia成为高性能计算的语言，这使得“硅谷”式大数据与人工智能（AI）计算、华尔街风格数字计算和国家实验室式科学计算之间的区别变得模糊。

Numerical software research enjoys the benefit of its fruits being quite practical. Those with decades of experience in the business know that users have been sharing code development long before GitHub or the use of the term “open source.”  

数值软件研究具有一定的实用性。那些具有几十年经验的企业，知道用户早在GitHub或“开码”一词使用前就已经开始共享代码开发了。

It has been a pleasure to nurture the Massachusetts Institute of Technology’s component of this worldwide effort and to experience the brilliant contributions from so many first-class researchers. Experience Julia for yourself by searching “Juliacon2015” online and watching the videos, trying juliabox.org, or visiting julialang.org.

**Acknowledgments:** I’d like to dedicate this article to my Ph.D. adviser and former SIAM President, Nick Trefethen, on the occasion of his 60th birthday.