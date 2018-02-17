---
layout: post
title: "[Wired] GREEDY, BRITTLE, OPAQUE, AND SHALLOW: THE DOWNSIDES TO DEEP LEARNING"
author: "李军"
categories: journal
tags: [wired, deep learning]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

**We've been promised a revolution in how and why nearly everything happens. But the limits of modern artificial intelligence are closer than we think.**

**我们已经预见几乎所有事情如何发生以及为什么发生的变革。但现代人工智能的极限比我们想象的要近得多。**

By <u>JASON PONTIN</u>

[an Ideas contributor for WIRED. He is a senior partner at Flagship Pioneering, a firm in Boston that creates, builds, and funds companies that solve problems in health, food, and sustainability. From 2004 to 2017 he was the editor in chief and publisher of MIT Technology Review. Before that he was the editor of Red Herring magazine, a business magazine that was popular during the dot-com boom.]

Feb 02, 2018

SUNDAR PICHAI, THE chief executive of Google, has said that AI “is more profound than … electricity or fire.” Andrew Ng, who founded Google Brain and now invests in AI startups, wrote that “If a typical person can do a mental task with less than one second of thought, we can probably automate it using AI either now or in the near future.”

谷歌的首席执行官桑达尔·皮查伊说人工智能“比电或火影响更深远。”创立了谷歌大脑，现投资人工智能初创公司的吴恩达写道：“如果一个普通人可以用不到一秒的思考时间做思维任务，那我们或许可以在现在或不久的将来使用人工智能来自动化。”

Their enthusiasm is pardonable. There have been remarkable advances in AI, after decades of frustration. Today we can tell a voice-activated personal assistant like Alexa to “Play the band Television,” or count on Facebook to tag our photographs; Google Translate is often almost as accurate as a human translator. Over the last half decade, billions of dollars in research funding and venture capital have flowed towards AI; it is the hottest course in computer science programs at MIT and Stanford. In Silicon Valley, newly minted AI specialists command half a million dollars in salary and stock.

他们的热情是可以原谅的。在经历了几十年的挫折之后，人工智能取得了显著的进步。今天，我们可以告诉像Alexa这样的一个用语音激活的个人助理“播放乐队电视”，或者依靠脸书给我们的照片贴上标签；谷歌翻译几乎和人类翻译一样准确。在过去的五年里，数十亿美元的研究资金和风险资本流向了人工智能，这是麻省理工学院和斯坦福大学最热门的计算机科学课程。在硅谷，新出道的人工智能专家就有50万美金的工资和股票。

But there are many things that people can do quickly that smart machines cannot. Natural language is beyond deep learning; new situations baffle artificial intelligences, like cows brought up short at a cattle grid. None of these shortcomings is likely to be solved soon. Once you’ve seen you’ve seen it, you can’t un-see it: deep learning, now the dominant technique in artificial intelligence, will not lead to an AI that abstractly reasons and generalizes about the world. By itself, it is unlikely to automate ordinary human activities.

但是有很多事情，人可以很快地做，而聪明的机器却不能。自然语言超出了深度学习；新的状况阻碍了人工智能，就像牛在拦牛木栅上长大一样。这些缺点都不可能很快得到解决。一旦你看到你已经看到了它，你就不能不看到它：现在已成为人工智能主要技术的深度学习，并不会产生抽象推理和概括世界的人工智能。就其本身而言，使普通人类活动自动化是不可能的。

To see why modern AI is good at a few things but bad at everything else, it helps to understand how deep learning works. Deep learning is math: a statistical method where computers learn to classify patterns using neural networks. Such networks possess inputs and outputs, a little like the neurons in our own brains; they are said to be “deep” when they possess multiple hidden layers that contain many nodes, with a blooming multitude of connections. Deep learning employs an algorithm called backpropagation, or backprop, that adjusts the mathematical weights between nodes, so that an input leads to the right output. In speech recognition, the phonemes c-a-t should spell the word “cat;” in image recognition, a photograph of a cat must not be labeled “a dog;” in translation, qui canem et faelem ut deos colunt should spit out “who worship dogs and cats as gods.” Deep learning is “supervised” when neural nets are trained to recognize phonemes, photographs, or the relation of Latin to English using millions or billions of prior, laboriously labeled examples.

为了解为什么现代人工智能擅长少数事情，而不擅长其他事情，理解深度学习如何工作是有帮助的。深度学习就是数学：计算机学习用神经网络对模式进行分类的一种统计方法。这样的网络具有输入和输出，有点像我们大脑中的神经元；当它们拥有多个包含许多节点的隐藏层，拥有大量的连接时，它们就被称为“深”。深度学习采用一种调整节点之间的数学权重，使输入产生正确的输出的被称为反向传播或backprop的算法。在语音识别中，音素c-a-t应该拼成单词 "cat"；在图像识别中，一只猫的照片不能被标记为"狗"；在翻译中，qui canem et faelem ut deos colunt应该快速说出“拜猫狗为神明的人”。当神经网络使用数百万或数十亿之前苦心标记的例子训练用来识别音素，照片，或拉丁语和英语间的关系时，深度学习就是“有监督的”。

Deep learning’s advances are the product of pattern recognition: neural networks memorize classes of things and more-or-less reliably know when they encounter them again. But almost all the interesting problems in cognition aren’t classification problems at all. “People naively believe that if you take deep learning and scale it 100 times more layers, and add 1000 times more data, a neural net will be able to do anything a human being can do,” says François Chollet, a researcher at Google. “But that’s just not true.”

深度学习的进步是模式识别的产物：神经网络记住事物的种类，或多或少可靠地知道它们何时再次出现。但是几乎所有有趣的认知问题都不是分类问题。谷歌研究员François Chollet说“人们天真地认为，如果你拿到深度学习，把它的层数扩大100倍以上，并把数据量增加1000倍以上，神经网络就能做人能做的任何事情，但事实并非如此。”

Gary Marcus, a professor of cognitive psychology at NYU and briefly director of Uber’s AI lab, recently published a remarkable trilogy of essays, offering a critical appraisal of deep learning. Marcus believes that deep learning is not “a universal solvent, but one tool among many.” And without new approaches, Marcus worries that AI is rushing toward a wall, beyond which lie all the problems that pattern recognition cannot solve. His views are quietly shared with varying degrees of intensity by most leaders in the field, with the exceptions of Yann LeCun, the director of AI research at Facebook, who curtly dismissed the argument as “all wrong,” and Geoffrey Hinton, a professor emeritus at the University of Toronto and the grandfather of backpropagation, who sees “no evidence” of a looming obstacle.

纽约大学认知心理学教授，Uber人工智能实验室的负责人Gary Marcus，最近发表了杰出的论文三部曲，对深度学习进行了批判性的评价。马库斯认为，深度学习不是“万能的溶剂，而只是许多工具中的一种”。马库斯担心没有新的方法，人工智能正朝着一堵墙冲去，这堵墙背后正是模式识别无法解决的所有问题。他的观点也悄然与该领域的大多数领导者不同程度的分享，除了无礼地认为该说法是“完全错误”的脸书人工智能研究主任Yann LeCun和认为看不到一个迫在眉睫的障碍“证据”的多伦多大学名誉教授、反向传播之父Geoffrey Hinton除外。

According to skeptics like Marcus, deep learning is greedy, brittle, opaque, and shallow. The systems are greedy because they demand huge sets of training data. Brittle because when a neural net is given a “transfer test”—confronted with scenarios that differ from the examples used in training—it cannot contextualize the situation and frequently breaks. They are opaque because, unlike traditional programs with their formal, debuggable code, the parameters of neural networks can only be interpreted in terms of their weights within a mathematical geography. Consequently, they are black boxes, whose outputs cannot be explained, raising doubts about their reliability and biases. Finally, they are shallow because they are programmed with little innate knowledge and possess no common sense about the world or human psychology.

像马库斯这样的怀疑论者认为，深度学习是贪心的、脆弱的、不透明的、肤浅的。这些系统很贪心，因为它们需要大量的训练数据。脆弱，因为当一个神经网络被给定不同于训练过程中用到的实例中会遇到的状况的“迁移测试”时，它不能将这种状况纳入上下文，并且频繁垮掉。它们是不透明的，因为不像传统的形式化、可调试代码的程序，神经网络的参数只能以数学形式的权重解释。因此，它们是黑盒，其输出不能被解释，这引起了人们对它们可靠性和偏差的怀疑。最后，它们是肤浅的，因为它们编程的知识很少，对世界或人的心理没有常识。

These limitations mean that a lot of automation will prove more elusive than AI hyperbolists imagine. “A self-driving car can drive millions of miles, but it will eventually encounter something new for which it has no experience,” explains Pedro Domingos, the author of The Master Algorithm and a professor of computer science at the University of Washington. “Or consider robot control: A robot can learn to pick up a bottle, but if it has to pick up a cup, it starts from scratch.” In January, Facebook abandoned M, a text-based virtual assistant that used humans to supplement and train a deep learning system, but never offered useful suggestions or employed language naturally.

这些局限意味着很多自动化将证明比AI运用夸张法的人想象的更难以捉摸。终极算法一书的作者、华盛顿大学计算机科学教授Pedro Domingos解释说，“自动驾驶汽车可以行驶数百万英里，但最终会遇到一些它没有经验的新事物，或者考虑机器人控制：机器人可以学习拿起瓶子，但如果它必须拿起一只杯子，那它就要从零开始了”。一月份，脸书中止了一个基于文本的虚拟助手M，它利用人类来补充和训练一个深度学习系统，但从来没有提供有用的建议或自然地使用语言。

What’s wrong? “It must be that we have a better learning algorithm in our heads than anything we’ve come up with for machines,” Domingos says. We need to invent better methods of machine learning, skeptics aver. The remedy for artificial intelligence, according to Marcus, is syncretism: combining deep learning with unsupervised learning techniques that don’t depend so much on labeled training data, as well as the old-fashioned description of the world with logical rules that dominated AI before the rise of deep learning. Marcus claims that our best model for intelligence is ourselves, and humans think in many different ways. His young children could learn general rules about language, and without many examples, but they were also born with innate capacities. “We are born knowing there are causal relationships in the world, that wholes can be made of parts, and that the world consists of places and objects that persist in space and time,” he says. “No machine ever learned any of that stuff using backprop.”

怎么了？Domingos说，“它必须是对于机器而言，我们在我们脑子里有一个比我们能想出的任何事情都好的学习算法”。怀疑论者断言，我们需要发明更好的机器学习方法。根据马库斯的说法，人工智能的补救之法是混合主义：将深度学习和不过多依赖标记训练数据的无监督学习技术相结合，以及将世界的老式描述与深度学习兴起前支配人工智能的逻辑规则相结合。马库斯声称我们最好的智能模型是我们自己，而人用很多不同的方式思考。他的孩子没有许多例子就可以学习语言的一般规则，这是他们天生的能力。他说，“我们生来就知道世界上有因果关系，整体由部分组成，世界由在时空中持续存在的地方和对象组成，从来没有机器使用反向传播学过这里的任何东西。”

Other researchers have different ideas. “We’ve used the same basic paradigms [for machine learning] since the 1950s,” says Pedro Domingos, “and at the end of the day, we’re going to need some new ideas.” Chollet looks for inspiration in program synthesis, programs that automatically create other programs. Hinton’s current research explores an idea he calls “capsules,” which preserves backpropagation, the algorithm for deep learning, but addresses some of its limitations.

其他研究人员有不同的想法。Pedro Domingos说，“自上世纪50年代以来，我们使用相同的基本范式[对于机器学习]，在一天结束的时候，我们需要一些新的想法。”Chollet在寻找程序合成(即，自动创建其他程序的程序)的灵感。Hinton目前的研究探讨一个他所谓“胶囊”的想法，它保留了深度学习的算法BP，但也处理了一些局限性。

“There are a lot of core questions in AI that are completely unsolved,” says Chollet, “and even largely unasked.” We must answer these questions because there are tasks that a lot of humans don’t want to do, such as cleaning toilets and classifying pornography, or which intelligent machines would do better, such as discovering drugs to treat diseases. More: there are things that we can’t do at all, most of which we cannot yet imagine.

Chollet说，“在人工智能中有很多完全未被解决的核心问题，甚至都没被提出来。”我们必须回答这些问题，因为有很多人不想做的任务，如打扫厕所和分类色情作品，或者智能机器可以做得更好，如发现治疗疾病的药物。更重要的是，有些事情我们根本做不到，其中大部分是我们无法想象的。

**AI Anxieties**

**人工智能焦虑**

+ You can stop panicking about a superhuman AI. As Kevin Kelly writes, that’s a myth.

+ 你可以停止担心超人AI。正如凯文·凯利所写，这是一个神话。

+ Another worry you can cross off your list? The fear that robots will take all of our jobs. It’s not nearly that simple.

+ 还有一个你可以从清单上划掉的担心吗？担心机器人会取代我们所有的工作。这并不是那么简单。

+ But AI is becoming an ever-more integral factor in the future of work. Say hello to your new AI coworkers.

+ 但是AI正在成为未来工作中不可或缺的因素。向你的新AI同事问好吧。