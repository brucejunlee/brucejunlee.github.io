---
layout: post
title: "[Quanta] New Theory Cracks Open the Black Box of Deep Learning"
author: "李军"
categories: journal
tags: [quanta, deep learning]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/quanta-InfoBottleneck-1.jpg)

A new idea called the “information bottleneck” is helping to explain the puzzling success of today’s artificial-intelligence algorithms — and might also explain how human brains learn.

一个被称为“信息瓶颈”的新想法有助于解释目前人工智能算法令人费解的成功，或许也能解释人脑是如何学习的。

By <u>Natalie Wolchover</u>

September 21, 2017

Even as machines known as “deep neural networks” have learned to converse, drive cars, beat video games and Go champions, dream, paint pictures and help make scientific discoveries, they have also confounded their human creators, who never expected so-called “deep-learning” algorithms to work so well. No underlying principle has guided the design of these learning systems, other than vague inspiration drawn from the architecture of the brain (and no one really understands how that operates either).

虽然“深度神经网络”这样的机器已经学会了交谈、开车、打视频游戏、击败围棋冠军、做梦、绘画以及帮助科学发现等，但它们也使人类创造者困惑不已，他们从没想到所谓的“深度学习”算法能够表现得如此好。除了来自大脑结构的模糊灵感（其实也没人真正理解它是如何运作的）外，没有任何基本原理能指导这些学习系统的设计。

Like a brain, a deep neural network has layers of neurons — artificial ones that are figments of computer memory. When a neuron fires, it sends signals to connected neurons in the layer above. During deep learning, connections in the network are strengthened or weakened as needed to make the system better at sending signals from input data — the pixels of a photo of a dog, for instance — up through the layers to neurons associated with the right high-level concepts, such as “dog.” After a deep neural network has “learned” from thousands of sample dog photos, it can identify dogs in new photos as accurately as people can. The magic leap from special cases to general concepts during learning gives deep neural networks their power, just as it underlies human reasoning, creativity and the other faculties collectively termed “intelligence.” Experts wonder what it is about deep learning that enables generalization — and to what extent brains apprehend reality in the same way.

像大脑一样，一个深度神经网络也有很多层神经元，只是这些神经元是人造的，它们只是计算机内存中凭空想象出来的事物。当一个神经元被激活时，它会向上层中与之相连的神经元发送信号。在深度学习期间，网络连接会按需加强或减弱以使系统更适合从输入数据（如一张狗照中的像素）中发送信号沿着网络层直到与正确的高级概念相关的神经元，如“狗”。一个深度神经网络从成千上万的狗照样本中学习后，它可以像人一样精确地从新的照片中识别出狗来。从特殊情况到一般概念的神奇飞跃赋能深度神经网络，就像它处于人类推理、创造力和其他一切被统称为“智能”的官能当中。专家不知道是什么使深度学习具有泛化能力，同时以相同的方式大脑能在多大程度上捕获到事实。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/quanta-InfoBottleneck-2.jpg)

Last month, a YouTube video of a conference talk in Berlin, shared widely among artificial-intelligence researchers, offered a possible answer. In the talk, Naftali Tishby, a computer scientist and neuroscientist from the Hebrew University of Jerusalem, presented evidence in support of a new theory explaining how deep learning works. Tishby argues that deep neural networks learn according to a procedure called the “information bottleneck,” which he and two collaborators first described in purely theoretical terms in 1999. The idea is that a network rids noisy input data of extraneous details as if by squeezing the information through a bottleneck, retaining only the features most relevant to general concepts. Striking new computer experiments by Tishby and his student Ravid Shwartz-Ziv reveal how this squeezing procedure happens during deep learning, at least in the cases they studied.

上个月，在柏林举行的一个会议演讲的YouTube视频，在人工智能研究者间广泛分享，它给出了一个可能答案。在演讲中，来自Hebrew University of Jerusalem的计算机科学家和神经科学家Naftali Tishby提供了证据用于支持一种解释深度学习如何工作的新理论。Tishby认为深度神经网络按照一个被称为“信息瓶颈”的过程来学习，他和两名合作者在1999年以纯理论的形式首次描述了该过程。想法是，一个网络可以消除含无关细节的带噪声输入数据，这就好像把信息挤过瓶颈，只剩下与一般概念最相关的特征。由Tishby和他的学生Ravid Shwartz-Ziv进行的全新计算机实验揭示了至少在他们的案例研究中，在深度学习期间这个挤压过程是如何发生的。

Tishby’s findings have the AI community buzzing. “I believe that the information bottleneck idea could be very important in future deep neural network research,” said Alex Alemi of Google Research, who has already developed new approximation methods for applying an information bottleneck analysis to large deep neural networks. The bottleneck could serve “not only as a theoretical tool for understanding why our neural networks work as well as they do currently, but also as a tool for constructing new objectives and architectures of networks,” Alemi said.

Tishby的发现使AI界兴奋不已。来自Google Research的Alex Alemi说“我相信，信息瓶颈的想法将在未来深度神经网络研究中非常重要”，他已经开发了新的近似方法将信息瓶颈分析应用到非常大的深度神经网络中。Alemi说瓶颈“不仅可以作为用来理解为什么我们的神经网络可以工作以及它们目前所做的一种理论工具，也可以作为构建网络新目标和架构的工具”。

Some researchers remain skeptical that the theory fully accounts for the success of deep learning, but Kyle Cranmer, a particle physicist at New York University who uses machine learning to analyze particle collisions at the Large Hadron Collider, said that as a general principle of learning, it “somehow smells right.”

一些研究者仍然对这个理论作为深度学习的全部原因持怀疑态度，来自New York University的粒子物理学家Kyle Cranmer说，作为学习的一般原则，它“听上去还是不错的”，他使用机器学习来分析大型强子对撞机中的粒子碰撞。

Geoffrey Hinton, a pioneer of deep learning who works at Google and the University of Toronto, emailed Tishby after watching his Berlin talk. “It’s extremely interesting,” Hinton wrote. “I have to listen to it another 10,000 times to really understand it, but it’s very rare nowadays to hear a talk with a really original idea in it that may be the answer to a really major puzzle.”

深度学习先驱Geoffrey Hinton，目前工作于Google和University of Toronto，他看完Tishby的柏林演讲后给他发了一封电邮。Hinton写道“这非常有趣，我还得再听10000遍才能真正理解，现在真的很少听到一个真正原创的谈话了，它可能是一个真正谜题的答案”。

According to Tishby, who views the information bottleneck as a fundamental principle behind learning, whether you’re an algorithm, a housefly, a conscious being, or a physics calculation of emergent behavior, that long-awaited answer “is that the most important part of learning is actually forgetting.”

根据Tishby（他将信息瓶颈视作学习背后的一个基本原则）的观点，无论你是一个算法、苍蝇、有意识的人或突发行为的物理计算，期待已久的回答是“学习中最重要的部分其实是遗忘”。

**The Bottleneck**

**瓶颈**

Tishby began contemplating the information bottleneck around the time that other researchers were first mulling over deep neural networks, though neither concept had been named yet. It was the 1980s, and Tishby was thinking about how good humans are at speech recognition — a major challenge for AI at the time. Tishby realized that the crux of the issue was the question of relevance: What are the most relevant features of a spoken word, and how do we tease these out from the variables that accompany them, such as accents, mumbling and intonation? In general, when we face the sea of data that is reality, which signals do we keep?

尽管还没有命名这些概念，但Tishby开始思考信息瓶颈的时候，其他研究者才刚开始考虑深度神经网络。那是在上世纪80年代，Tishby正在思考人们对语音识别的擅长程度，这是那时AI的主要挑战。Tishby意识到，问题的难点在相关性：一个词最相关的特征是什么，我们如何从伴随它们的变量（如口音，咕哝和语调等）中将它们梳理出来？一般来说，当我们面对现实的数据时，我们会保留哪些信号呢？

“This notion of relevant information was mentioned many times in history but never formulated correctly,” Tishby said in an interview last month. “For many years people thought information theory wasn’t the right way to think about relevance, starting with misconceptions that go all the way to Shannon himself.”

Tishby在上个月的采访中说，“相关信息的概念历史上已经多次提及，但却从没有正确地表达出来，多年来，人们一直认为信息论并不是思考相关性的正确方法，这一误解开始于香农本人”。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/quanta-InfoBottleneck-3.jpg)

Naftali Tishby, a professor of computer science at the Hebrew University of Jerusalem.

Claude Shannon, the founder of information theory, in a sense liberated the study of information starting in the 1940s by allowing it to be considered in the abstract — as 1s and 0s with purely mathematical meaning. Shannon took the view that, as Tishby put it, “information is not about semantics.” But, Tishby argued, this isn’t true. Using information theory, he realized, “you can define ‘relevant’ in a precise sense.”

信息论的创始人Claude Shannon，在某种意义上解放了信息研究，他允许在抽象层面（即纯数学意义的1s和0s）上考虑信息，该研究始于上世纪40年代。正如Tishby上面所说，香农认为，“信息与语义无关”。但是，Tishby认为，这不是真的。他认识到，利用信息论，“你可以精确定义‘相关’”。

Imagine X is a complex data set, like the pixels of a dog photo, and Y is a simpler variable represented by those data, like the word “dog.” You can capture all the “relevant” information in X about Y by compressing X as much as you can without losing the ability to predict Y. In their 1999 paper, Tishby and co-authors Fernando Pereira, now at Google, and William Bialek, now at Princeton University, formulated this as a mathematical optimization problem. It was a fundamental idea with no killer application.

假设X是一个复杂的数据集，如狗照中的像素，Y是由这些数据表示的一个简单变量，如单词“狗”。你可以通过尽可能不失对Y的预测能力地压缩X，来捕获X中所有关于Y的“相关”信息。Tishby和共同作者Fernando Pereira（现在Google）和William Bialek（现在Princeton University）在他们1999年的论文中，将此构造成一个数学优化问题。那时这是一个没有杀手级应用的基本思想。

“I’ve been thinking along these lines in various contexts for 30 years,” Tishby said. “My only luck was that deep neural networks became so important.”

Tishby说，“我在不同上下文中沿着这些思路已经思考30年了，我唯一的幸运是深度神经网络变得如此重要”。

**Eyeballs on Faces on People on Scenes**

Though the concept behind deep neural networks had been kicked around for decades, their performance in tasks like speech and image recognition only took off in the early 2010s, due to improved training regimens and more powerful computer processors. Tishby recognized their potential connection to the information bottleneck principle in 2014 after reading a surprising paper by the physicists David Schwab and Pankaj Mehta.

尽管深度神经网络背后的概念已经被谈论了几十年，但它们在语音、图像等任务中的性能由于改进的训练方案和更强大的计算机处理器，在2010年代初才突飞猛进。Tishby在2014年读完物理学家David Schwab和Pankaj Mehta写的一篇令人惊奇的论文后发现它们与信息瓶颈原理之间的潜在联系。

The [duo discovered](https://www.quantamagazine.org/deep-learning-relies-on-renormalization-physicists-find-20141204/) that a deep-learning algorithm invented by Hinton called the “deep belief net” works, in a particular case, exactly like renormalization, a technique used in physics to zoom out on a physical system by coarse-graining over its details and calculating its overall state. When Schwab and Mehta applied the deep belief net to a model of a magnet at its “critical point,” where the system is fractal, or self-similar at every scale, they found that the network automatically used the renormalization-like procedure to discover the model’s state. It was a stunning indication that, as the biophysicist Ilya Nemenman said at the time, “extracting relevant features in the context of statistical physics and extracting relevant features in the context of deep learning are not just similar words, they are one and the same.”

[他们发现](https://www.quantamagazine.org/deep-learning-relies-on-renormalization-physicists-find-20141204/)，由Hinton发明的一种被称为“深度信念网络”的深度学习算法，在重整化（一种在物理中使用的通过粗粒化细节计算其整体状态从而实现在物理系统上进行缩放的技术）这样的特殊情况下可以起作用。当Schwab和Mehta将深度信念网络运用到一个处于“临界点”的磁铁模型（此时系统在每个尺度上都是分形的或自相似的）时，他们发现网络自动应用类重整化过程来发现模型状态。正如生物物理学家Ilya Nemenman当时所说，这是一个惊人的迹象，它表明，“在统计物理中提取相关特征和在深度学习中提取相关特征不单单只是相似，他们就是同一件事。”

The only problem is that, in general, the real world isn’t fractal. “The natural world is not ears on ears on ears on ears; it’s eyeballs on faces on people on scenes,” Cranmer said. “So I wouldn’t say [the renormalization procedure] is why deep learning on natural images is working so well.” But Tishby, who at the time was undergoing chemotherapy for pancreatic cancer, realized that both deep learning and the coarse-graining procedure could be encompassed by a broader idea. “Thinking about science and about the role of my old ideas was an important part of my healing and recovery,” he said.

唯一的问题是，一般来说，现实世界不是分形的。Cranmer说，“自然世界并不是ears on ears on ears on ears；而是eyeballs on faces on people on scenes，所以我不认为[重整化过程]是自然图像上深度学习表现如此好的原因”。但当时正在接受胰腺癌化疗的Tishby，意识到深度学习和粗粒化过程可以包含在一个更广泛的想法中。他说：“思考科学和我的旧想法在这些问题上的作用是我治疗和康复的重要部分”。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/quanta-InfoBottleneck-4.jpg)

Noga Zaslavsky, left, and Ravid Shwartz-Ziv helped develop the information bottleneck theory of deep learning as graduate students of Naftali Tishby’s.

In 2015, he and his student Noga Zaslavsky hypothesized that deep learning is an information bottleneck procedure that compresses noisy data as much as possible while preserving information about what the data represent. Tishby and Shwartz-Ziv’s new experiments with deep neural networks reveal how the bottleneck procedure actually plays out. In one case, the researchers used small networks that could be trained to label input data with a 1 or 0 (think “dog” or “no dog”) and gave their 282 neural connections random initial strengths. They then tracked what happened as the networks engaged in deep learning with 3,000 sample input data sets.

2015年，他和他的学生Noga Zaslavsky认为，深度学习就是一个尽可能压缩带噪声的数据同时保留数据表征信息的信息瓶颈算法。Tishby和Shwartz-Ziv的深度神经网络新实验揭示了瓶颈过程是如何真正发挥作用的。在一个例子中，研究人员使用了小型网络，我们可以训练该网络对输入数据打上标签1或0（认为“是狗”或“不是狗”），并给它们282个神经连接赋予随机初始强度。然后它们随着网络致力于包含3000个样本输入数据集的深度学习时追踪网络发生了什么。

The basic algorithm used in the majority of deep-learning procedures to tweak neural connections in response to data is called “stochastic gradient descent”: Each time the training data are fed into the network, a cascade of firing activity sweeps upward through the layers of artificial neurons. When the signal reaches the top layer, the final firing pattern can be compared to the correct label for the image — 1 or 0, “dog” or “no dog.” Any differences between this firing pattern and the correct pattern are “back-propagated” down the layers, meaning that, like a teacher correcting an exam, the algorithm strengthens or weakens each connection to make the network layer better at producing the correct output signal. Over the course of training, common patterns in the training data become reflected in the strengths of the connections, and the network becomes expert at correctly labeling the data, such as by recognizing a dog, a word, or a 1.

大多数深度学习过程中用到的调整神经连接以响应数据的基本算法被称为“随机梯度下降”：每次将训练数据送入网络时，一连串激活活动将往上扫过很多层人工神经元。当信号到达顶层时，最后的激活模式将与图像的正确标签（1或0，“是狗”或“不是狗”）进行比较。激活模式和正确模式之间的任何差异都将“反向传播”回网络层中，意思是说，像批改试卷的老师一样，算法增强或削弱每个连接使网络层更好地产生正确的输出信号。随着训练的进行，训练数据中的共同模式将反映在连接强度上，网络则成为正确标注数据的专家，如通过识别一条狗、一个单词或一个1。

In their experiments, Tishby and Shwartz-Ziv tracked how much information each layer of a deep neural network retained about the input data and how much information each one retained about the output label. The scientists found that, layer by layer, the networks converged to the information bottleneck theoretical bound: a theoretical limit derived in Tishby, Pereira and Bialek’s original paper that represents the absolute best the system can do at extracting relevant information. At the bound, the network has compressed the input as much as possible without sacrificing the ability to accurately predict its label.

在他们的实验中，Tishby和Shwartz-Ziv追踪了深度神经网络的每一层保留了多少输入数据信息和输出标签信息。科学家们发现，网络会逐层收敛到信息瓶颈的理论界限，即在Tishby、Pereira和Bialek的原始论文中推导的理论极限，它表示在抽取相关信息时系统能做到的绝对最佳值。在界限处，网络尽可能压缩输入，而不牺牲准确预测其标签的能力。

Tishby and Shwartz-Ziv also made the intriguing discovery that deep learning proceeds in two phases: a short “fitting” phase, during which the network learns to label its training data, and a much longer “compression” phase, during which it becomes good at generalization, as measured by its performance at labeling new test data.

Tishby和Shwartz-Ziv也得到了这样一个有趣的发现，即深层学习分两阶段进行：一个短的“拟合”阶段，在此期间网络学习标注训练数据，和一个更长的“压缩”阶段，正如在标注新的测试数据时性能测量一样，在此期间它擅长泛化。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/quanta-InfoBottleneck-5.jpg)

As a deep neural network tweaks its connections by stochastic gradient descent, at first the number of bits it stores about the input data stays roughly constant or increases slightly, as connections adjust to encode patterns in the input and the network gets good at fitting labels to it. Some experts have compared this phase to memorization.

当深度神经网络通过随机梯度下降调整其连接时，首先，随着调整连接以编码输入中的模式，网络很好地拟合标签和输入，但它存储的关于输入数据的位数大致保持不变或略有增加。一些专家把这一阶段与记忆进行了比较。

Then learning switches to the compression phase. The network starts to shed information about the input data, keeping track of only the strongest features — those correlations that are most relevant to the output label. This happens because, in each iteration of stochastic gradient descent, more or less accidental correlations in the training data tell the network to do different things, dialing the strengths of its neural connections up and down in a random walk. This randomization is effectively the same as compressing the system’s representation of the input data. As an example, some photos of dogs might have houses in the background, while others don’t. As a network cycles through these training photos, it might “forget” the correlation between houses and dogs in some photos as other photos counteract it. It’s this forgetting of specifics, Tishby and Shwartz-Ziv argue, that enables the system to form general concepts. Indeed, their experiments revealed that deep neural networks ramp up their generalization performance during the compression phase, becoming better at labeling test data. (A deep neural network trained to recognize dogs in photos might be tested on new photos that may or may not include dogs, for instance.)

然后学习进入到压缩阶段。网络开始摆脱输入数据的信息，只追踪最强的特征（即那些与输出标签最相关的关系）。这是因为，在随机梯度下降的每次迭代中，训练数据中或多或少的偶然相关性指示网络做不同的事情，随机上下拨动神经连接的强度。这种随机化实际上与压缩输入数据的系统表示是相同的。举个例子，一些狗照中也许背景有房子，而其它照片没有。当网络循环处理这些训练照片时，它或许会“忘记”一些照片中房子和狗之间的关系，因为其它照片没有。Tishby和Shwartz-Ziv认为，就是这种特定的遗忘，使系统形成了一般概念。事实上，他们的实验表明，在压缩阶段深度神经网络提高了泛化性能，从而更好地标注测试数据。（例如，一种训练用于识别照片中狗的深度神经网络可以在新的包括或不包括狗的照片中进行测试）。

It remains to be seen whether the information bottleneck governs all deep-learning regimes, or whether there are other routes to generalization besides compression. Some AI experts see Tishby’s idea as one of many important theoretical insights about deep learning to have emerged recently. Andrew Saxe, an AI researcher and theoretical neuroscientist at Harvard University, noted that certain very large deep neural networks don’t seem to need a drawn-out compression phase in order to generalize well. Instead, researchers program in something called early stopping, which cuts training short to prevent the network from encoding too many correlations in the first place.

信息瓶颈是否支配所有深度学习机制，或除压缩外是否还有其它泛化途径都有待观察。一些人工智能专家将Tishby的想法视作最近出现的众多重要的关于深度学习的理论见解之一。Harvard University 人工智能研究者和理论神经科学家Andrew Saxe指出，一些非常大的深度神经网络似乎不需要漫长的压缩阶段也能为了泛化得很好。相反，研究人员在一些被称为“提前停止”的事情中进行编程，它通过突然打断训练来防止网络在一开始就编码过多的相关性。

Tishby argues that the network models analyzed by Saxe and his colleagues differ from standard deep neural network architectures, but that nonetheless, the information bottleneck theoretical bound defines these networks’ generalization performance better than other methods. Questions about whether the bottleneck holds up for larger neural networks are partly addressed by Tishby and Shwartz-Ziv’s most recent experiments, not included in their preliminary paper, in which they train much larger, 330,000-connection-deep neural networks to recognize handwritten digits in the 60,000-image Modified National Institute of Standards and Technology database, a well-known benchmark for gauging the performance of deep-learning algorithms. The scientists saw the same convergence of the networks to the information bottleneck theoretical bound; they also observed the two distinct phases of deep learning, separated by an even sharper transition than in the smaller networks. “I’m completely convinced now that this is a general phenomenon,” Tishby said.

Tishby认为Saxe和他的同事分析的网络模型不同于标准深度神经网络结构，但尽管如此，信息瓶颈的理论界限还是比其他方法更好地定义了这些网络的泛化性能。Tishby和Shwartz-Ziv的最新实验部分解决了更大的神经网络是否拥有瓶颈的问题，但这些不包含在他们最初的论文中，在那篇论文中，他们训练了更大的具有330000个连接的深度神经网络在拥有60000张图片的MNIST（Modified National Institute of Standards and Technology，这是度量深度学习算法性能的一个著名基准）数据库中识别手写数字。科学家们看到了网络同样收敛到信息瓶颈的理论界限；他们也观察到了深度学习中由一个骤然转变而非更小网络所分割的两个不同阶段。Tishby说，“我完全相信这是一个一般现象”。

**Humans and Machines**

**人机**

The mystery of how brains sift signals from our senses and elevate them to the level of our conscious awareness drove much of the early interest in deep neural networks among AI pioneers, who hoped to reverse-engineer the brain’s learning rules. AI practitioners have since largely abandoned that path in the mad dash for technological progress, instead slapping on bells and whistles that boost performance with little regard for biological plausibility. Still, as their thinking machines achieve ever greater feats — even stoking fears that AI could someday pose an existential threat — many researchers hope these explorations will uncover general insights about learning and intelligence.

大脑如何从我们的感官中筛选信号并将其提升到我们的意识水平的奥秘激发了AI先驱早期对深度神经网络的大量兴趣，他们希望对大脑的学习规则进行逆向工程。人工智能从业者自那以后很大程度上放弃了技术进展的疯狂冲刺那条路，进而选择那些提升性能的方法，并没有考虑生物合理性。不过，因为他们的思维机器实现了更大的功绩，甚至引发了AI某天会构成实际威胁的担忧-许多研究者希望这些探索将揭开学习和智力的一般见解。

**"The most important part of learning is actually forgetting." - Naftali Tishby**

**“学习中最重要的部分就是遗忘。” - Naftali Tishby**

Brenden Lake, an assistant professor of psychology and data science at New York University who studies similarities and differences in how humans and machines learn, said that Tishby’s findings represent “an important step towards opening the black box of neural networks,” but he stressed that the brain represents a much bigger, blacker black box. Our adult brains, which boast several hundred trillion connections between 86 billion neurons, in all likelihood employ a bag of tricks to enhance generalization, going beyond the basic image- and sound-recognition learning procedures that occur during infancy and that may in many ways resemble deep learning.

New York University 心理学和数据科学助理教授Brenden Lake，他研究了人机学习的异同，说Tishby的发现是“揭开神经网络黑盒的重要一步”，但他强调，大脑是一个更大的更昏暗的黑盒。我们成人的大脑，在860亿神经元间拥有几百万亿连接，它很可能利用一套技巧来增强泛化能力，这超出了发生在婴儿期的基本图像和声音识别学习过程，这在许多方面都类似于深度学习。

For instance, Lake said the fitting and compression phases that Tishby identified don’t seem to have analogues in the way children learn handwritten characters, which he studies. Children don’t need to see thousands of examples of a character and compress their mental representation over an extended period of time before they’re able to recognize other instances of that letter and write it themselves. In fact, they can learn from a single example. Lake and his colleagues’ models suggest the brain may deconstruct the new letter into a series of strokes — previously existing mental constructs — allowing the conception of the letter to be tacked onto an edifice of prior knowledge. “Rather than thinking of an image of a letter as a pattern of pixels and learning the concept as mapping those features” as in standard machine-learning algorithms, Lake explained, “instead I aim to build a simple causal model of the letter,” a shorter path to generalization.

例如，Lake说Tishby发现的拟合和压缩阶段，似乎与他研究的儿童学习手写字符的方式不相似。儿童不需要看一个字符成千上万个例子，在能够识别字符的其它实例前不需要在较长的一段时间内压缩他们的心理表征就能自己写出来。事实上，他们可以从单个例子中学习。Lake和他同事的模型表明，大脑可以将新的字母解构成一系列笔画（它是先前存在的内心构造），它允许将字母的概念列入先验知识大厦中。Lake解释到，就像在标准机器学习算法中一样，“不是将一个字母图像看作一个像素模式，并学习映射这些特征的概念，相反，我的目的是建立一个简单的字母因果模型，作为一个更短的泛化路径”。

Such brainy ideas might hold lessons for the AI community, furthering the back-and-forth between the two fields. Tishby believes his information bottleneck theory will ultimately prove useful in both disciplines, even if it takes a more general form in human learning than in AI. One immediate insight that can be gleaned from the theory is a better understanding of which kinds of problems can be solved by real and artificial neural networks. “It gives a complete characterization of the problems that can be learned,” Tishby said. These are “problems where I can wipe out noise in the input without hurting my ability to classify. This is natural vision problems, speech recognition. These are also precisely the problems our brain can cope with.”

如此聪明的想法可能会给AI界带来经验教训，进一步穿梭在这两个领域间。Tishby认为他的信息瓶颈理论最终将对这两个学科都有用，即使它在人类学习中比在AI中需要一个更一般的形式。从理论中可以得到的一个直接见解是可以更好地理解真实神经网络和人工神经网络可以解决哪类问题。Tishby说，“这给出了可学习问题的一个完整刻画”。这些是“我可以消除输入噪音而不影响分类能力的问题。这是自然视觉问题、语音识别。这些恰好也是我们大脑能够处理的问题”。

Meanwhile, both real and artificial neural networks stumble on problems in which every detail matters and minute differences can throw off the whole result. Most people can’t quickly multiply two large numbers in their heads, for instance. “We have a long class of problems like this, logical problems that are very sensitive to changes in one variable,” Tishby said. “Classifiability, discrete problems, cryptographic problems. I don’t think deep learning will ever help me break cryptographic codes.”

同时，真实神经网络和人工神经网络都存在问题，这里每一个细节问题都起作用，微小的差异都可能导致整个结果崩溃。例如，大多数人不能很快地进行两个大数的乘法。Tishby说，“我们有一大类这样的问题，如对某个变量变化非常敏感的逻辑问题、分类问题、离散问题以及加密问题等。我不认为深度学习会帮助我破解密码”。

Generalizing — traversing the information bottleneck, perhaps — means leaving some details behind. This isn’t so good for doing algebra on the fly, but that’s not a brain’s main business. We’re looking for familiar faces in the crowd, order in chaos, salient signals in a noisy world.

穿越信息瓶颈的泛化大概意味着丢弃一些细节。这对代数运算来说不是太好，但这不是大脑的主要职责。我们正在寻觅人群中熟悉的面孔，混乱中的秩序，嘈杂的世界中的显著信号。

This article was reprinted on Wired.com.



