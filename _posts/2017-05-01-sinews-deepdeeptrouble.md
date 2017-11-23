---
layout: post
title: "[SIAM NEWS] Deep, Deep Trouble"
author: "李军"
categories: journal
tags: [siam, deep learning]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

**Deep Learning’s Impact on Image Processing, Mathematics, and Humanity**

**深度学习对图像处理，数学和人类的影响**

By <u>Michael Elad</u>

May 01, 2017

[Michael Elad is a professor in the Computer Science Department at the Technion – Israel Institute of Technology. He is editor-in-chief of the SIAM Journal on Imaging Sciences.]

I am really confused. I keep changing my opinion on a daily basis, and I cannot seem to settle on one solid view of this puzzle. No, I am not talking about world politics or the current U.S. president, but rather something far more critical to humankind, and more specifically to our existence and work as engineers and researchers. I am talking about…deep learning.

我真的非常困惑。我每天都在改变我的观点，我似乎无法得到这个难题的一个可靠观点。不，我不是在谈论世界政治或现任美国总统，而是对人类，更具体地说是我们作为工程师和研究人员存在，更为重要的事情。我正在谈论的是深度学习。

While you might find the above statement rather bombastic and overstated, deep learning indeed raises several critical questions we must address. In the following paragraphs, I hope to expose one key conflict related to the emergence of this field, which is relevant to researchers in the image processing community.

虽然你可能会发现上面所说有些华而不实和夸大其词，但深度学习的确提出了几个我们必须解决的关键问题。下面，我希望揭露与该领域出现相关的一个关键冲突，这与图像处理社区的研究人员有关。

First, a few words about deep learning to put our discussion into perspective. Neural networks have been around for decades, proposing a universal learning mechanism that could, in principle, fit to any learnable data source. In its feed-forward architecture, layers of perceptrons—also referred to as neurons—first perform weighted averaging of their inputs, followed by nonlinearities such as a sigmoid or rectified-linear curves. One can train this surprisingly simple system to fit a given input set to its desired output, serving various supervised regression and classification problems.

首先，我们来谈谈深度学习。神经网络已经存在几十年了，它给出了一个原则上能够拟合任何可学习的数据源的通用学习机制。在前馈架构中，多层感知机（也被称为神经元）首先进行输入的加权平均，然后进行非线性操作，如sigmoid或ReLU。人们可以训练这个极其简单的系统来拟合给定输入集到期望输出，并且对大量的监督回归和分类问题都有用。

All of this may sound great, but unfortunately this concept did not take off in the 1980s and 90s — it simply did not provide a sufficiently competitive performance. In addition, the emergence of support vector machines for learning tasks, accompanied by solid theoretical foundations and a convex optimization formulation, seemed to be the last nail in the coffin. Eventually, neural networks entered a long hibernation period. Only a few persistent researchers—Yann LeCun (New York Univerity and Facebook), Geoffrey Hinton (University of Toronto), Yoshua Bengio (University of Montreal), and Jürgen Schmidhuber (Dalle Molle Institute for Artificial Intelligence Research)—stayed in this arena, insisting on trying to convince this seemingly doomed method to behave better. Several important architectures, such as convolutional and long short-term memory networks, resulted from their efforts; yet they were still confined to a niche. Then neural networks suddenly came back, and with a vengeance.

一切听上去不错，但不幸的是这个概念在上世纪八九十年代并没有流行起来，因为它并不能提供足够的竞争力。此外，伴随着坚实的理论基础和凸优化，学习任务中SVM的出现似乎成了棺材板上的最后一颗钉子。最终，神经网络进入了漫长的冬眠期。只有很少一些研究人员，如Yann LeCun (New York Univerity and Facebook)， Geoffrey Hinton (University of Toronto)， Yoshua Bengio (University of Montreal) and Jürgen Schmidhuber (Dalle Molle Institute for Artificial Intelligence Research)等一直留在这个领域，坚持试图使人相信这个方法能够表现得更好。一些重要的架构，如CNN和LSTM就来源于他们的努力；但他们仍局限于一片区域。然后神经网络突然出乎意料地回来了。

A series of papers during the early 2000s suggested the successful application of this architecture, leading to state-of-the-art results in practically any assigned task. Key aspects in these contributions included the following: the use of many network layers, which explains the term “deep learning”; a huge amount of data on which to train; massive computations typically run on computer clusters or graphic processing units; and wise optimization algorithms that employ effective initializations and gradual stochastic gradient learning. Unfortunately, all of these great empirical achievements were obtained with hardly any theoretical understanding of the underlying paradigm. Moreover, the optimization employed in the learning process is highly non-convex and intractable from a theoretical viewpoint.

21世纪初一系列论文都表明了这种在实践中为任何任务带来目前最好结果的架构的成功应用。这些贡献的关键方面包括：许多网络层的使用，这恰恰说明了“深度学习”一词；一个用于训练的巨大数据量；通常运行在计算机集群或GPUs上的海量计算；以及采用有效初始化和渐进随机梯度学习的明智的优化算法。不幸的是，所有这些伟大的经验成就的获得对基本范式都几乎没有任何理论的理解。此外，在学习过程中采用的优化是高度非凸的，并且从理论来看很难处理。

This application effort began with written digit recognition (see Figure 1), moving slowly and carefully to more challenging visual and speech recognition and natural language processing tasks, and from there on to practically anything that could be cast as a supervised learning task. Companies such as Google, Facebook, and Microsoft quickly realized the potential in this field and invested massive manpower and budget in order to master these tools and exploit them in their products. On the academic front, conferences in signal processing, image processing, and computer vision have become deep learning playgrounds, contributing to a growing dominance of this bread of work.

这个应用工作始于手写数字识别（见图1），然后缓慢而谨慎地进行更具挑战性的视觉、语音识别和自然语言处理任务，并且从那开始一直到任何可以转化成监督学习任务的场景。谷歌、Facebook和微软等公司很快就意识到了这一领域的潜力，并投入大量人力和预算，以掌握这些工具并在其产品中加以利用。在学术领域，信号处理、图像处理和计算机视觉的会议已经成为深度学习的场所，从而促进了这一工作的日益增长的统治。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-deepdeeptrouble-1.jpg)

**Figure 1.** Neural networks have shown great potential, first in character recognition and subsequently in many other tasks. Image credit: Michael Elad.

This history brings us to present day. For the sake of brevity, consider the classic image processing task of denoising — removing noise from an image (see Figure 2). Thousands of papers addressing this fundamental task were written over the years. Researchers developed beautiful and deep mathematical ideas with tools from partial differential equations, such as anisotropic diffusion and total variation, energy minimization viewpoint, adoption of a geometric interpretation of images as manifolds, use of the Beltrami flow, and more. Harmonic analysis and approximation theory have also served the denoising task, leading to major breakthroughs with wavelet theory and sparse representations. Other brilliant ideas included low-rank approximation, non-local means, Bayesian estimation, and robust statistics. We have hence gained vast knowledge in image processing over the past three decades, impacting many other image processing tasks and effectively upgrading this field to be mathematically well-founded.

这段历史把我们带到今天。为了简洁起见，让我们考虑图像去噪（即从图像中去除噪声）这个经典的图像处理任务（见图2）。多年来已经有数以千计的论文来处理这项基本任务。研究人员利用PDEs工具开发了非常漂亮深奥的数学思想，如各向异性扩散和总变差，能量最小化观点，采用流形作为图像的几何解释，Beltrami流等等。调和分析和逼近理论也为去噪任务提供了帮助，使用小波理论和稀疏表示取得了重大突破。其他优秀的思想包括低秩近似、非局部均值、贝叶斯估计和健壮统计。因此，我们在过去的三十年中获得了大量的图像处理知识，这影响了许多其他的图像处理任务，并有效地提高了这一领域的数学基础。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-deepdeeptrouble-2.jpg)

**Figure 2.** A denoising example. Left. An original image (public domain). Middle. Image contaminated by additive Gaussian noise of STD=100. Right. The denoising outcome obtained by one of the leading algorithms — the BM3D [1]. Image credit: Michael Elad.

In 2012, Harold Burger, Christian Schuler, and Stefan Harmeling decided to throw deep learning into this problem. The idea was conceptually quite simple: take a huge set of clean images, add synthetic noise, and then feed them to the learning process that aims to turn a noisy image into its clean version. While the process was tedious, frustrating, and lengthy—tweaking the method’s parameters in a search for good performance likely took a long time—the end result was a network that performed better than any known image denoising algorithm at that time.

2012年，Harold Burger，Christian Schuler，和Stefan Harmeling决定把深度学习引入这个问题中。这个想法概念上非常简单：取一组干净的图片，加上合成噪声，然后把它们输入学习过程中，目的是把带有噪声的图像变成干净的版本。虽然这个过程冗长乏味，令人沮丧，并且在寻找良好性能的过程中对方法参数进行了长时间调整，但最终结果是一个比任何已知的图像去噪算法都要好的网络。

The above is not an isolated story. Today, deep learning treats many other image processing needs, with unsurpassed results. This is true for single image super-resolution, demosaicing, deblurring, segmentation, image annotation, and face recognition, among others.

上面并不是一个孤立的故事。今天，深度学习处理许多其他图像处理需求，具有无与伦比的结果。这对于单幅图像超分辨率，插值，复原、分割、图像标注和人脸识别等都已经实现。

Should we be happy about this trend? Well, if we are in the business of solving practical problems such as noise removal, the answer must be positive. Right? Therefore, a company seeking such a solution should be satisfied. But what about us scientists? What is the true objective behind the vast effort that we invested in the image denoising problem? Yes, we do aim for effective noise-removal algorithms, but this constitutes a small fraction of our motivation, as we have a much wider and deeper agenda. Researchers in our field aim to understand the data on which we operate. This is done by modeling information in order to decipher its true dimensionality and manifested phenomena. Such models serve denoising and other problems in image processing, but far more than that, they allow identifying new ways to extract knowledge from the data and enable new horizons.

我们应该对这种趋势感到高兴吗？好吧，如果我们正在解决噪音去除等实际问题，答案肯定是肯定的。对吗？因此，正寻求这样一个解决方案的公司应该是满意的。但对于我们科学家呢？我们在图像去噪问题上投入大量精力的真正目的是什么？是的，我们的目标是有效的去噪算法，但这只是我们的一小部分动机，因为我们有一个更广泛更深入的议程。我们这个研究领域的研究人员旨在了解我们操作的数据，这是通过对信息建模来实现的，目的是解释它真实的维度和表象。这样的模型有助于去噪和图像处理中的其他问题，但远不止于此，它们允许识别从数据中提取知识并启用新视野的新方法。

Now back to the main question: should we be pleased about emerging solutions based on deep learning? Is our frustration justified? What is the role of deep learning in imaging science? These questions present themselves when researchers in the community meet at conferences, and the answers are diverse and confusing. The facts speak loudly for themselves; in most cases, deep learning-based solutions lack mathematical elegance and offer very little interpretability of the found solution or understanding of the underlying phenomena. On the positive side, however, the performance obtained is terrific. This is clearly not the school of research we have been taught, and not the kind of science we want to practice. Should we insist on our more rigorous ways, even at the cost of falling behind in terms of output quality? Or should we fight back and seek ways to fuse ideas from deep learning into our more solid foundations?

现在回到主要问题：我们是否应该对基于深度学习的新兴解决方案感到高兴呢？我们的不满意是正当的吗？深度学习在图像科学中的作用是什么？当本社区的研究人员在会议上开会时，这些问题就出现了，答案也五花八门，令人困惑。还是让事实来说话吧；在大多数情况下，基于深度学习的解决方案缺乏数学的优雅，对于发现的解决方案或底层现象的理解几乎很难提供解释。然而从积极的方面来说，取得的成绩是惊人的。这显然不是我们所学的研究流派，也不是我们想要实践的那种科学。我们是否应该坚持更严格的方式，即使是以牺牲产品质量为代价呢？或者我们应该反击，寻求把来自深度学习的思想融合进我们更坚实的基础吗？

To further complicate this story, certain deep learning-based contributions bear some elegance that cannot be dismissed. Such is the case with the style-transfer problem, which yielded amazingly beautiful results, and with inversion ideas of learned networks used to synthesize images out of thin air, as Google’s Deep Dream project does. A few years ago we did not have the slightest idea how to formulate such complicated tasks; now they are solved formidably as a byproduct of a deep neural network trained for the completely extraneous task of visual classification.

为了使这个故事进一步复杂化，某些基于深度学习的贡献具有不可忽视的优雅性。这是一个风格迁移问题的例子，这个问题产生了令人惊讶的漂亮结果，并使用了从稀薄的空气中合成图像的学习网络的逆向思维，就像谷歌的Deep Dream项目那样。几年前，我们完全不知道如何制定这样的复杂任务；现在它们已经被解决了，并作为一个训练用于完全无关的视觉分类任务的深度神经网络的副产品。

From my personal viewpoint, image processing researchers have mixed feelings of disgust and envy towards this recent trend of deep learning that keeps pushing itself into our court. Some of us have chosen to remain bystanders for now, while others play along and divert their research agendas accordingly. I belong to the latter group, with some restrictions. In my opinion, it is impossible to imagine that this wave will pass without a marked influence on our field. Thus, I allow deep learning to influence my research team’s thoughts and actions, but we continue to insist on seeking mathematical elegance and a clear understanding of the ideas we develop. Time will tell if we are aiming for the impossible.

从我个人的观点来看，图像处理研究人员对最近这种深度学习的趋势感到厌恶和嫉妒。我们中的一些人现在仍然选择旁观，而另一些人则相应地转变了他们的研究议程。我属于后者。在我看来，很难想象这波浪潮不会对我们的领域造成影响。因此，我允许深度学习影响我的研究团队的思想和行动，但我们仍然坚持寻求数学的优雅，并清楚地理解我们开发的想法。时间会告诉我们是否我们的目标是不可能的。

Briefly circling back to my opening statement on deep learning’s massive impact on humankind, human lives will likely be very different several decades into the future. Humanoid robots and intelligence systems might surround us and influence many of our activities, employment and jobs may be things of the past, and relationships between people will probably change drastically. To put it bluntly, your grandchild is likely to have a robot spouse. And here is the punch line: much of the technology behind this bizarre future is likely to emerge from deep learning and its descendant fields.

简单回顾一下我开头关于深度学习对人类巨大影响的言论，未来几十年人类的生活将大不相同。人形机器人和智能系统也许会包围我们，影响我们的许多活动，就业和工作可能将成过去，人际关系可能会发生重大变化。坦率地说，你的孙子很可能有一个机器人配偶。这里是Punch Line喜剧俱乐部：在这个奇异的未来背后，许多技术可能会从深度学习和它的后继领域中涌现出来。

While this technology progresses rapidly, we haven’t stopped to think if this is the future we want for ourselves. The curiosity and tremendous talent of engineers and researchers is driving us towards this future, as do companies that see profit as their main goal. How is it that we rarely engage in discussion about regulating or controlling this progress and guiding it towards a desired future? This is a matter for a different article.

虽然这项技术进展很快，但我们并没有停下来思考是否这就是我们自己想要的未来。工程师和研究人员的好奇心和巨大的天赋驱使我们朝着这个未来前进，同样，那些把利润作为主要目标的公司也是如此。如果我们很少讨论校准或控制这一过程并引导它走向一个理想的未来事情将如何呢？这是另一篇文章的问题。

What are your thoughts on the impact of deep learning on image processing — and humanity? Share your feedback by sending us a letter to the editor or blog post at sinews@siam.org, or post a comment below.

**Acknowledgments:** The author would like to thank Alex Bronstein and Ron Kimmel for valuable comments, which helped tune the message of this article.

References

[1] Dabov, K., Foi, A., Katkovnik, V., & Egiazarian, K. (2007). Color image denoising via sparse 3D collaborative filtering with grouping constraint in luminance-chrominance space. Proc. IEEE Int. Conf. Image Process., 1, I-313-I-316.