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

根据Tishby（他将信息瓶颈视作学习背后的一个基本原则）的观点，无论你是一个算法、苍蝇、有意识的人或突发行为的物理计算，期待已久的回答是“学习中最重要的部分其实是遗忘。”

**The Bottleneck**

**瓶颈**

Tishby began contemplating the information bottleneck around the time that other researchers were first mulling over deep neural networks, though neither concept had been named yet. It was the 1980s, and Tishby was thinking about how good humans are at speech recognition — a major challenge for AI at the time. Tishby realized that the crux of the issue was the question of relevance: What are the most relevant features of a spoken word, and how do we tease these out from the variables that accompany them, such as accents, mumbling and intonation? In general, when we face the sea of data that is reality, which signals do we keep?

Tishby开始思考信息瓶颈的时候，其他的研究者首先考虑的深度神经网络，虽然概念已经命名但。It was the 1980s, and Tishby was thinking about how good humans are at speech recognition — a major challenge for AI at the time. Tishby意识到，问题的关键是关联的问题：一个词最相关的特征是什么，以及我们如何捉弄这些从伴随他们的变量，如口音，含糊的语调？一般来说，当我们面对现实的数据时，我们会保留哪些信号？

“This notion of relevant information was mentioned many times in history but never formulated correctly,” Tishby said in an interview last month. “For many years people thought information theory wasn’t the right way to think about relevance, starting with misconceptions that go all the way to Shannon himself.”

“这对相关信息的概念被多次提及历史上却没有制定正确的，”Tishby在接受采访时说的最后一个月。“很多年来，人们认为信息理论不是正确的方法来考虑相关性，从误解一直到香农自己开始。”

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/quanta-InfoBottleneck-3.jpg)

Naftali Tishby, a professor of computer science at the Hebrew University of Jerusalem.

Claude Shannon, the founder of information theory, in a sense liberated the study of information starting in the 1940s by allowing it to be considered in the abstract — as 1s and 0s with purely mathematical meaning. Shannon took the view that, as Tishby put it, “information is not about semantics.” But, Tishby argued, this isn’t true. Using information theory, he realized, “you can define ‘relevant’ in a precise sense.”

Claude Shannon，信息论的创始人，在某种意义上解放了信息的研究在上世纪40年代开始允许它是抽象的是1和0的纯数学意义。香农认为，正如Tishby所说，“信息不是语义。”但是，Tishby认为，这不是真的。利用信息理论，他认识到，“你可以在精确的意义上定义‘相关’。”

Imagine X is a complex data set, like the pixels of a dog photo, and Y is a simpler variable represented by those data, like the word “dog.” You can capture all the “relevant” information in X about Y by compressing X as much as you can without losing the ability to predict Y. In their 1999 paper, Tishby and co-authors Fernando Pereira, now at Google, and William Bialek, now at Princeton University, formulated this as a mathematical optimization problem. It was a fundamental idea with no killer application.

如果x是一个复杂的数据集，如狗的照片的像素，和Y是一个简单的变量的数据表示，像“狗”。你可以通过压缩x尽可能不失预测Y在1999纸的能力捕捉所有的“相关”信息x关于Y，Tishby和共同作者Fernando Pereira，现在在谷歌，和William Bialek，现在在普林斯顿大学，制定这一数学优化问题。这是一个没有杀手级应用的基本思想。

“I’ve been thinking along these lines in various contexts for 30 years,” Tishby said. “My only luck was that deep neural networks became so important.”

“我一直在想沿着这些线路在不同的上下文中的30年，”Tishby说。“我唯一的幸运是深深的神经网络变得如此重要。”

**Eyeballs on Faces on People on Scenes**

**场景中人脸上的眼球**

Though the concept behind deep neural networks had been kicked around for decades, their performance in tasks like speech and image recognition only took off in the early 2010s, due to improved training regimens and more powerful computer processors. Tishby recognized their potential connection to the information bottleneck principle in 2014 after reading a surprising paper by the physicists David Schwab and Pankaj Mehta.

尽管背后深层神经网络的概念已经踢了几十年了，他们的任务，如语音和图像的识别性能，只有开始在本世纪初，由于改进的训练方案和更强大的计算机处理器。Tishby认可他们的潜在联系的信息瓶颈原理2014阅读后由物理学家David Schwab和Pankaj Mehta惊讶了。

The duo discovered that a deep-learning algorithm invented by Hinton called the “deep belief net” works, in a particular case, exactly like renormalization, a technique used in physics to zoom out on a physical system by coarse-graining over its details and calculating its overall state. When Schwab and Mehta applied the deep belief net to a model of a magnet at its “critical point,” where the system is fractal, or self-similar at every scale, they found that the network automatically used the renormalization-like procedure to discover the model’s state. It was a stunning indication that, as the biophysicist Ilya Nemenman said at the time, “extracting relevant features in the context of statistical physics and extracting relevant features in the context of deep learning are not just similar words, they are one and the same.”

他们发现，深度学习算法由Hinton发明的叫“坚定信念网”的作品，在特定的情况下，完全像重整化，用于物理缩小在一个物理系统的粗粒化的细节和计算其整体状态的技术。当施瓦布和梅塔应用网一个磁铁模型深入信仰在其“临界点”，系统是分形，自相似或在每一个规模，他们发现网络自动应用重整化程序发现模型的状态。这是一个惊人的迹象表明，作为生物物理学家Ilya Nemenman当时表示，“在统计物理中提取相关的特征，在深入学习中提取相关的特征是不一样的话，他们是同一个。”

The only problem is that, in general, the real world isn’t fractal. “The natural world is not ears on ears on ears on ears; it’s eyeballs on faces on people on scenes,” Cranmer said. “So I wouldn’t say [the renormalization procedure] is why deep learning on natural images is working so well.” But Tishby, who at the time was undergoing chemotherapy for pancreatic cancer, realized that both deep learning and the coarse-graining procedure could be encompassed by a broader idea. “Thinking about science and about the role of my old ideas was an important part of my healing and recovery,” he said.

唯一的问题是，一般来说，现实世界不是分形的。“自然世界是不是耳朵耳朵耳朵耳朵；它在人们对场景的面孔吸引眼球，”Cranmer说。“所以我不会说[重整化程序]是为什么对自然图像的深度学习工作那么好。”但Tishby当时接受胰腺癌化疗，意识到深度学习和粗粒化过程可以用一个更广泛的概念包括。他说：“思考科学和旧观念的作用是我康复和康复的重要组成部分。”。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/quanta-InfoBottleneck-4.jpg)

Noga Zaslavsky, left, and Ravid Shwartz-Ziv helped develop the information bottleneck theory of deep learning as graduate students of Naftali Tishby’s.

In 2015, he and his student Noga Zaslavsky hypothesized that deep learning is an information bottleneck procedure that compresses noisy data as much as possible while preserving information about what the data represent. Tishby and Shwartz-Ziv’s new experiments with deep neural networks reveal how the bottleneck procedure actually plays out. In one case, the researchers used small networks that could be trained to label input data with a 1 or 0 (think “dog” or “no dog”) and gave their 282 neural connections random initial strengths. They then tracked what happened as the networks engaged in deep learning with 3,000 sample input data sets.

在2015，他和他的学生Noga Zaslavsky认为，深度学习是一个信息瓶颈算法压缩数据噪声的同时尽可能保留数据代表了什么信息。Tishby和Shwartz Ziv的新实验揭示深层神经网络的瓶颈工序，真正发挥出。在一个例子中，研究人员使用小型网络，可以训练输入1或0（认为“狗”或“没有狗”）的输入数据，并给出他们的282个神经连接随机初始强度。然后他们追踪了3000个样本输入数据集进行深入学习的情况。

The basic algorithm used in the majority of deep-learning procedures to tweak neural connections in response to data is called “stochastic gradient descent”: Each time the training data are fed into the network, a cascade of firing activity sweeps upward through the layers of artificial neurons. When the signal reaches the top layer, the final firing pattern can be compared to the correct label for the image — 1 or 0, “dog” or “no dog.” Any differences between this firing pattern and the correct pattern are “back-propagated” down the layers, meaning that, like a teacher correcting an exam, the algorithm strengthens or weakens each connection to make the network layer better at producing the correct output signal. Over the course of training, common patterns in the training data become reflected in the strengths of the connections, and the network becomes expert at correctly labeling the data, such as by recognizing a dog, a word, or a 1.

大多数深层学习过程中用于调整神经连接以响应数据的基本算法被称为“随机梯度下降”：每次训练数据送入网络时，一连串的放电活动通过人工神经元层向上扫。当信号到达顶层，最后的射击模式可以比较形象的正确标签的1或0，“狗”或“没有狗”。这种射击模式和正确的模式之间的任何差异是“传播”图层，即像老师批改考试的算法，加强或削弱每个连接使网络层更好的产生正确的输出信号。在训练过程中，训练数据中常见的模式反映在连接的优点上，而网络则成为正确标记数据的专家，例如通过识别一个狗、一个单词或一个1。

In their experiments, Tishby and Shwartz-Ziv tracked how much information each layer of a deep neural network retained about the input data and how much information each one retained about the output label. The scientists found that, layer by layer, the networks converged to the information bottleneck theoretical bound: a theoretical limit derived in Tishby, Pereira and Bialek’s original paper that represents the absolute best the system can do at extracting relevant information. At the bound, the network has compressed the input as much as possible without sacrificing the ability to accurately predict its label.

在他们的实验中，Tishby和Shwartz Ziv跟踪多少信息，每层深度神经网络的输入数据和保留多少信息，每一个保留的输出标签。科学家们发现，一层一层的网络融合的信息瓶颈理论的结合：理论上的限制来自Tishby、Pereira和韦克的原始论文，代表绝对最好的系统可以在提取相关信息。在绑定时，网络尽可能地压缩输入，而不牺牲准确预测其标签的能力。

Tishby and Shwartz-Ziv also made the intriguing discovery that deep learning proceeds in two phases: a short “fitting” phase, during which the network learns to label its training data, and a much longer “compression” phase, during which it becomes good at generalization, as measured by its performance at labeling new test data.

Shwartz Ziv也做出了有趣Tishby发现深层学习分为两个阶段：一个简短的“拟合”的阶段，在这期间网络学习标签的训练数据，和一个更长的“压缩”阶段，在这期间很好的推广，其性能在新的测试测量数据标记。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/quanta-InfoBottleneck-5.jpg)

As a deep neural network tweaks its connections by stochastic gradient descent, at first the number of bits it stores about the input data stays roughly constant or increases slightly, as connections adjust to encode patterns in the input and the network gets good at fitting labels to it. Some experts have compared this phase to memorization.

当一个深的神经网络通过随机梯度下降调整其连接时，首先，它存储的关于输入数据的比特数大致保持不变或略有增加，因为连接调整到输入中的编码模式，网络很好地对其进行标记。一些专家把这一阶段与记忆进行了比较。

Then learning switches to the compression phase. The network starts to shed information about the input data, keeping track of only the strongest features — those correlations that are most relevant to the output label. This happens because, in each iteration of stochastic gradient descent, more or less accidental correlations in the training data tell the network to do different things, dialing the strengths of its neural connections up and down in a random walk. This randomization is effectively the same as compressing the system’s representation of the input data. As an example, some photos of dogs might have houses in the background, while others don’t. As a network cycles through these training photos, it might “forget” the correlation between houses and dogs in some photos as other photos counteract it. It’s this forgetting of specifics, Tishby and Shwartz-Ziv argue, that enables the system to form general concepts. Indeed, their experiments revealed that deep neural networks ramp up their generalization performance during the compression phase, becoming better at labeling test data. (A deep neural network trained to recognize dogs in photos might be tested on new photos that may or may not include dogs, for instance.)

然后学习切换到压缩阶段。网络开始传递关于输入数据的信息，只跟踪最强的特性——那些与输出标签最相关的特性。这是因为，在每次随机梯度下降的迭代中，训练数据中或多或少的偶然相关性告诉网络做不同的事情，随机地在随机游动中上下地连接神经连接的强度。这种随机化实际上与压缩系统对输入数据的表示相同。举个例子，一些狗的照片可能有背景的房子，而其他的照片没有。作为一个网络周期通过这些训练照片，它可能“忘记”一些照片之间的房子和狗之间的关系，因为其他照片抵消它。正是这种遗忘的细节，Tishby和Shwartz Ziv说，使系统形成的一般概念。事实上，他们的实验表明，深神经网络在压缩阶段提高了泛化性能，从而更好地标记测试数据。（例如，一种训练用于识别照片中狗的深层神经网络可能会在新的照片中进行测试，例如可能包括或不包括狗在内）。

It remains to be seen whether the information bottleneck governs all deep-learning regimes, or whether there are other routes to generalization besides compression. Some AI experts see Tishby’s idea as one of many important theoretical insights about deep learning to have emerged recently. Andrew Saxe, an AI researcher and theoretical neuroscientist at Harvard University, noted that certain very large deep neural networks don’t seem to need a drawn-out compression phase in order to generalize well. Instead, researchers program in something called early stopping, which cuts training short to prevent the network from encoding too many correlations in the first place.

信息瓶颈是否制约着所有深层学习机制，或者除了压缩之外是否还有其他泛化途径有待观察。一些人工智能专家看到Tishby的思想作为一种关于深入学习了许多重要的理论见解，最近出现了。Andrew Saxe，一个AI研究员、哈佛大学理论神经科学家指出，一些非常大的深度神经网络似乎不需要旷日持久的压缩阶段为了推广。相反，研究人员在一种叫做“提前停止”的项目中进行编程，这种训练缩短了训练时间，以防止网络在一开始就编码过多的相关性。

Tishby argues that the network models analyzed by Saxe and his colleagues differ from standard deep neural network architectures, but that nonetheless, the information bottleneck theoretical bound defines these networks’ generalization performance better than other methods. Questions about whether the bottleneck holds up for larger neural networks are partly addressed by Tishby and Shwartz-Ziv’s most recent experiments, not included in their preliminary paper, in which they train much larger, 330,000-connection-deep neural networks to recognize handwritten digits in the 60,000-image Modified National Institute of Standards and Technology database, a well-known benchmark for gauging the performance of deep-learning algorithms. The scientists saw the same convergence of the networks to the information bottleneck theoretical bound; they also observed the two distinct phases of deep learning, separated by an even sharper transition than in the smaller networks. “I’m completely convinced now that this is a general phenomenon,” Tishby said.

Tishby认为网络模型由Saxe和他的同事分析了不同标准的深层神经网络结构，但是，尽管如此，信息瓶颈理论界定义这些网络的泛化性能优于其他方法。是否拥有了更大的神经网络的瓶颈是由Tishby和Shwartz Ziv的最新实验部分解决问题，不包括在他们的初步研究，在他们的火车大得多，330000个连接的深度神经网络识别手写体数字60000的图像修改国家标准与技术研究院测量数据库，深度学习算法性能的一个著名的基准。科学家们看到了同样的网络收敛到信息瓶颈理论的界限；他们也观察到了两个不同阶段的深层学习，被一个更为尖锐的过渡所分割，而不是更小的网络。“我完全相信这是一个普遍的现象，”Tishby说。

**Humans and Machines**

**人与机器**

The mystery of how brains sift signals from our senses and elevate them to the level of our conscious awareness drove much of the early interest in deep neural networks among AI pioneers, who hoped to reverse-engineer the brain’s learning rules. AI practitioners have since largely abandoned that path in the mad dash for technological progress, instead slapping on bells and whistles that boost performance with little regard for biological plausibility. Still, as their thinking machines achieve ever greater feats — even stoking fears that AI could someday pose an existential threat — many researchers hope these explorations will uncover general insights about learning and intelligence.

大脑如何从我们的感官中筛选信号并将其提升到我们的意识水平的奥秘，激发了早期对神经网络初学者的兴趣，他们希望逆向工程大脑的学习规则。人工智能从业者在很大程度上放弃了在技术进步的疯狂冲刺中的那条路，而不是在生物学的合理性方面对性能的提高起到了积极的作用。不过，他们的思维机器实现更大的功勋，甚至引发担心AI会构成现实的威胁-许多研究者希望这些探索将揭开关于学习和智力的一般见解。

**"The most important part of learning is actually forgetting." - Naftali Tishby**

**“学习中最重要的部分就是遗忘” - Naftali Tishby**

Brenden Lake, an assistant professor of psychology and data science at New York University who studies similarities and differences in how humans and machines learn, said that Tishby’s findings represent “an important step towards opening the black box of neural networks,” but he stressed that the brain represents a much bigger, blacker black box. Our adult brains, which boast several hundred trillion connections between 86 billion neurons, in all likelihood employ a bag of tricks to enhance generalization, going beyond the basic image- and sound-recognition learning procedures that occur during infancy and that may in many ways resemble deep learning.

Brenden Lake，心理学助理教授和数据科学在纽约大学谁在人类和机器学习研究的异同，说Tishby的发现是“走向开放的神经网络的黑箱的重要一步，”但他强调，大脑是一个更大的、黑的黑盒子。我们的成人大脑，它拥有860亿个神经元之间的数亿连接，很可能利用一套技巧来增强概括，超越基本的图像和声音识别学习过程，发生在婴儿期，可能在许多方面类似于深刻的学习。

For instance, Lake said the fitting and compression phases that Tishby identified don’t seem to have analogues in the way children learn handwritten characters, which he studies. Children don’t need to see thousands of examples of a character and compress their mental representation over an extended period of time before they’re able to recognize other instances of that letter and write it themselves. In fact, they can learn from a single example. Lake and his colleagues’ models suggest the brain may deconstruct the new letter into a series of strokes — previously existing mental constructs — allowing the conception of the letter to be tacked onto an edifice of prior knowledge. “Rather than thinking of an image of a letter as a pattern of pixels and learning the concept as mapping those features” as in standard machine-learning algorithms, Lake explained, “instead I aim to build a simple causal model of the letter,” a shorter path to generalization.

例如，湖说拟合和压缩阶段，Tishby确定似乎不在孩子学习手写的方式类似，他研究。孩子们不需要看到成千上万个字符的例子，在他们能够识别出字母的其他实例并自己书写之前，在较长的一段时间内压缩他们的心理表征。事实上，他们可以从一个例子中学习。湖和他的同事的模型表明，大脑可以解构为一系列新的字母笔画-先前存在的精神构造允许信才能列入先验知识大厦的概念。湖心岛解释说，“而不是将一个字母的图像看作像素的模式，并将这些概念作为映射这些特征的概念，就像在标准机器学习算法中一样，”我解释说，我的目标是建立一个简单的“因果模型”，即“概括的一个更短的路径”。

Such brainy ideas might hold lessons for the AI community, furthering the back-and-forth between the two fields. Tishby believes his information bottleneck theory will ultimately prove useful in both disciplines, even if it takes a more general form in human learning than in AI. One immediate insight that can be gleaned from the theory is a better understanding of which kinds of problems can be solved by real and artificial neural networks. “It gives a complete characterization of the problems that can be learned,” Tishby said. These are “problems where I can wipe out noise in the input without hurting my ability to classify. This is natural vision problems, speech recognition. These are also precisely the problems our brain can cope with.”

这样聪明的想法可能会对智能社区的经验教训，深化来回两个领域之间。Tishby认为他的信息瓶颈理论最终将在这两个学科是有用的，即使它需要一个更一般的形式，在人类的学习比在AI。从理论中可以得到的一个直接的见解是更好地理解哪种问题可以通过真实神经网络和人工神经网络来解决。“这表明了可以学到一个完整的表征问题，”Tishby说。这些是“我可以在输入中消除噪音而不影响分类能力的问题”。这是自然视觉问题，语音识别。这些也正是我们的大脑能够应付的问题。”

Meanwhile, both real and artificial neural networks stumble on problems in which every detail matters and minute differences can throw off the whole result. Most people can’t quickly multiply two large numbers in their heads, for instance. “We have a long class of problems like this, logical problems that are very sensitive to changes in one variable,” Tishby said. “Classifiability, discrete problems, cryptographic problems. I don’t think deep learning will ever help me break cryptographic codes.”

同时，真实神经网络和人工神经网络都存在问题，每一个细节问题和微小的差异都可能导致整个结果的崩溃。例如，大多数人不能很快地将两个大数相乘。“我们有一个很长的类这样的问题，逻辑的问题，是一个变量的变化非常敏感，”Tishby说。“分类、离散问题，密码问题。我不认为深度学习会帮助我破解密码。”

Generalizing — traversing the information bottleneck, perhaps — means leaving some details behind. This isn’t so good for doing algebra on the fly, but that’s not a brain’s main business. We’re looking for familiar faces in the crowd, order in chaos, salient signals in a noisy world.

概括——穿越信息瓶颈，也许意味着留下一些细节。这对代数运算不是很好，但这不是大脑的主要业务。我们在人群中寻找熟悉的面孔，在混乱中寻找秩序，在嘈杂的世界中寻找显著的信号。

This article was reprinted on Wired.com.



