---
layout: post
title: "[MIT Technology Review] The Dark Secret at the Heart of AI"
author: "李军"
categories: journal
tags: [mit, AI, machine learning, deep learning]
image:
  feature: 
  teaser: 
  credit: 
  creditlink: ""
---

No one really knows how the most advanced algorithms do what they do. That could be a problem.

没人真正知道最高级的算法是如何做它们要做的事的。那可能是个问题。

by <u>Will Knight</u> 

April 11, 2017

[I am the senior editor for AI at MIT Technology Review. I mainly cover machine intelligence, robots, and automation, but I’m interested in most aspects of computing. I grew up in south London, and I wrote my first line of code (a spell-binding infinite loop) on a mighty Sinclair ZX Spectrum. Before joining this publication, I worked as the online editor at New Scientist magazine.] 

Last year, a strange self-driving car was released onto the quiet roads of Monmouth County, New Jersey. The experimental vehicle, developed by researchers at the chip maker Nvidia, didn’t look different from other autonomous cars, but it was unlike anything demonstrated by Google, Tesla, or General Motors, and it showed the rising power of artificial intelligence. The car didn’t follow a single instruction provided by an engineer or programmer. Instead, it relied entirely on an algorithm that had taught itself to drive by watching a human do it.

去年，一辆奇怪的自动驾驶汽车被投放在Monmouth County, New Jersey安静的路上。由芯片制造商Nvidia公司的研究员开发的实验车与其它无人驾驶汽车看上去没什么不同，但它不同于谷歌、特斯拉或通用汽车展示的任何产品，它显示了人工智能的能力在不断增强。那辆汽车没有按照工程师或程序员提供的单一指令进行操作。相反，它完全依赖于一种通过观察人类行为来自学驾驶的算法。

Getting a car to drive this way was an impressive feat. But it’s also a bit unsettling, since it isn’t completely clear how the car makes its decisions. Information from the vehicle’s sensors goes straight into a huge network of artificial neurons that process the data and then deliver the commands required to operate the steering wheel, the brakes, and other systems. The result seems to match the responses you’d expect from a human driver. But what if one day it did something unexpected—crashed into a tree, or sat at a green light? As things stand now, it might be difficult to find out why. The system is so complicated that even the engineers who designed it may struggle to isolate the reason for any single action. And you can’t ask it: there is no obvious way to design such a system so that it could always explain why it did what it did.

这样开车是个了不起的壮举。但它也有点令人不安，因为现在还不完全清楚汽车是如何作决定的。来自车辆传感器的信息直接进入到一个巨大的人工神经元网络中，它处理这些数据，然后传送操作方向盘、刹车以及其他系统所需的指令。结果似乎与人类驾驶员的反应相吻合。但是如果有一天它做一些出乎意料的事情，如撞到一棵树上，或者绿灯时还停着不动呢？就目前情况来看，可能很难找到原因。这个系统太复杂了，以至于设计它的工程师们也很难从任何一个动作中分离出原因。当然你也不能问它：没有明显的方法来设计这样一个系统以至于它总能解释它为什么这么做。

The mysterious mind of this vehicle points to a looming issue with artificial intelligence. The car’s underlying AI technology, known as deep learning, has proved very powerful at solving problems in recent years, and it has been widely deployed for tasks like image captioning, voice recognition, and language translation. There is now hope that the same techniques will be able to diagnose deadly diseases, make million-dollar trading decisions, and do countless other things to transform whole industries.

这辆车神秘的大脑指出了人工智能的一个迫在眉睫的问题。汽车的基本人工智能技术，即深度学习，已被证明在解决近年来存在的问题时非常有效，并已被广泛部署于图像标题、语音识别以及语言翻译等任务中。现在人们希望，同样的技术能够诊断出致命疾病，做出百万美元的交易决定以及无数其它的事情来改变整个行业。

But this won’t happen—or shouldn’t happen—unless we find ways of making techniques like deep learning more understandable to their creators and accountable to their users. Otherwise it will be hard to predict when failures might occur—and it’s inevitable they will. That’s one reason Nvidia’s car is still experimental.

但是，这种情况并不会发生或不应该发生，除非我们能找到一些方法使深度学习这样的技术对于它们的创造者更好理解，并能对用户做出解释。否则很难预测什么时候会发生故障，这是不可避免的。这也是Nvidia的汽车仍处于试验阶段的一个原因。

Already, mathematical models are being used to help determine who makes parole, who’s approved for a loan, and who gets hired for a job. If you could get access to these mathematical models, it would be possible to understand their reasoning. But banks, the military, employers, and others are now turning their attention to more complex machine-learning approaches that could make automated decision-making altogether inscrutable. Deep learning, the most common of these approaches, represents a fundamentally different way to program computers. “It is a problem that is already relevant, and it’s going to be much more relevant in the future,” says Tommi Jaakkola, a professor at MIT who works on applications of machine learning. “Whether it’s an investment decision, a medical decision, or maybe a military decision, you don’t want to just rely on a ‘black box’ method.”

数学模型已经被用来帮助决定假释谁，批准谁获取贷款以及雇佣谁等。如果你能接触到这些数学模型，就有可能理解它们的原因。但银行、军队、企业主和其它机构现在正把注意力转移到可以自动决策的更复杂的机器学习方法，这使得一切完全难以捉摸。深度学习作为最常用的方法，它代表了编程计算机的一种完全不同的方法。MIT致力于机器学习应用的教授Tommi Jaakkola说：“这是一个有意义的问题，未来将变得更有意义。无论是投资决策、医疗决策，还是军事决策，你都不想仅仅依赖于‘黑盒’方法”。

There’s already an argument that being able to interrogate an AI system about how it reached its conclusions is a fundamental legal right. Starting in the summer of 2018, the European Union may require that companies be able to give users an explanation for decisions that automated systems reach. This might be impossible, even for systems that seem relatively simple on the surface, such as the apps and websites that use deep learning to serve ads or recommend songs. The computers that run those services have programmed themselves, and they have done it in ways we cannot understand. Even the engineers who build these apps cannot fully explain their behavior.

已经有一个论点认为，能够询问人工智能系统如何得出结论是一项基本的法律权利。从2018年夏天开始，欧盟可能要求公司能够对自动化系统得出的决策向用户作出解释。这也许是不可能的，即使是表面上看起来比较简单的系统，如使用深度学习来提供广告或推荐歌曲的应用程序和网站。运行这些服务的计算机已经进行了自我编程，它们以我们无法理解的方式完成了这些工作。即使是构建这些应用的工程师也不能完全解释它们的行为。

This raises mind-boggling questions. As the technology advances, we might soon cross some threshold beyond which using AI requires a leap of faith. Sure, we humans can’t always truly explain our thought processes either—but we find ways to intuitively trust and gauge people. Will that also be possible with machines that think and make decisions differently from the way a human would? We’ve never before built machines that operate in ways their creators don’t understand. How well can we expect to communicate—and get along with—intelligent machines that could be unpredictable and inscrutable? These questions took me on a journey to the bleeding edge of research on AI algorithms, from Google to Apple and many places in between, including a meeting with one of the great philosophers of our time.

这就提出了令人难以置信的问题。随着技术的进步，我们可能很快就会跨过一个门槛，那时使用人工智能需要极大的信心。当然，我们人类并不总能真正解释我们的思维过程，但我们可以找到凭直觉信任和判断人的方法。能否造出与人类思考决策的方式不同的机器呢？我们以前从未制造过以创造者不能理解的方式运行的机器。我们希望能和或许不可预知、神秘莫测的智能机器沟通相处得多好呢？这些问题将我带到了人工智能算法研究的前沿，从谷歌到苹果，还有许多地方，包括与我们这个时代的一个伟大哲学家的会面。 

In 2015, a research group at Mount Sinai Hospital in New York was inspired to apply deep learning to the hospital’s vast database of patient records. This data set features hundreds of variables on patients, drawn from their test results, doctor visits, and so on. The resulting program, which the researchers named Deep Patient, was trained using data from about 700,000 individuals, and when tested on new records, it proved incredibly good at predicting disease. Without any expert instruction, Deep Patient had discovered patterns hidden in the hospital data that seemed to indicate when people were on the way to a wide range of ailments, including cancer of the liver. There are a lot of methods that are “pretty good” at predicting disease from a patient’s records, says Joel Dudley, who leads the Mount Sinai team. But, he adds, “this was just way better.”

2015年，纽约Mount Sinai Hospital的一个研究组受到启发，将深度学习运用到医院庞大的病历数据库中。这个数据集从病人的测试结果、医生访问等信息中刻画了关于病人的数百个变量的特征。相应的被研究人员命名为Deep Patient的项目使用大约700000个人的数据进行训练，当对新记录进行测试时，结果表明它在预测疾病方面表现得非常好。没有任何专家的指导，Deep Patient发现了隐藏在医院数据中的模式，这些数据似乎表明人们正在走向各种各样的疾病，包括肝癌。领导Mount Sinai团队的Joel Dudley说，有很多方法可以从病人的病历中预测疾病。但他补充说，“这只是更好的方式。”

**“We can build these models, but we don’t know how they work.”**

**“我们可以建立这些模型，但我们不知道它们是如何工作的。”**

At the same time, Deep Patient is a bit puzzling. It appears to anticipate the onset of psychiatric disorders like schizophrenia surprisingly well. But since schizophrenia is notoriously difficult for physicians to predict, Dudley wondered how this was possible. He still doesn’t know. The new tool offers no clue as to how it does this. If something like Deep Patient is actually going to help doctors, it will ideally give them the rationale for its prediction, to reassure them that it is accurate and to justify, say, a change in the drugs someone is being prescribed. “We can build these models,” Dudley says ruefully, “but we don’t know how they work.”

同时，Deep Patient也有点令人费解。它似乎对精神分裂症等精神紊乱的发作预测得非常好。但是，由于精神分裂症众所周知对医生而言是很难预测的，Dudley想知道这是如何做到的。他还是不知道。新工具并没有提供关于它是如何运行的线索。如果像Deep Patient这样的产品能实际帮助医生，它将给他们提供理想的预测依据，使他们确信这是准确的，并证明为某人开的处方药物的改变。Dudley沮丧地说：“我们可以建立这些模型，但我们不知道它们是如何工作的。”

Artificial intelligence hasn’t always been this way. From the outset, there were two schools of thought regarding how understandable, or explainable, AI ought to be. Many thought it made the most sense to build machines that reasoned according to rules and logic, making their inner workings transparent to anyone who cared to examine some code. Others felt that intelligence would more easily emerge if machines took inspiration from biology, and learned by observing and experiencing. This meant turning computer programming on its head. Instead of a programmer writing the commands to solve a problem, the program generates its own algorithm based on example data and a desired output. The machine-learning techniques that would later evolve into today’s most powerful AI systems followed the latter path: the machine essentially programs itself.

人工智能并非一直如此。一开始，关于AI应该如何理解或解释有两个思想学派。许多人认为根据规则和逻辑来构建推理机器是最有意义的，这使得那些关心检查代码的人能够看到它们的内部运行机制。另一些人则认为，如果机器从生物学中获得灵感，并通过观察和经验来学习，那么智能就会更容易出现。这意味着要在开始转变计算机编程。程序根据实例数据和期望输出生成自己的算法，而不是程序员编写命令来解决问题。后来发展成为今天最强大的人工智能系统的机器学习技术就遵循后一种方法：机器本质上是自我编程的。

At first this approach was of limited practical use, and in the 1960s and ’70s it remained largely confined to the fringes of the field. Then the computerization of many industries and the emergence of large data sets renewed interest. That inspired the development of more powerful machine-learning techniques, especially new versions of one known as the artificial neural network. By the 1990s, neural networks could automatically digitize handwritten characters.

起初，这种方法的实际应用有限，在上世纪6、70年代，它基本上只局限于领域边缘。之后，许多行业的计算机化和大型数据集的出现重新燃起了人们的兴趣。这启发了更强大的机器学习技术的发展，特别是一种称为人工神经网络的新版本。到20世纪90年代，神经网络可以自动数字化手写字符。

But it was not until the start of this decade, after several clever tweaks and refinements, that very large—or “deep”—neural networks demonstrated dramatic improvements in automated perception. Deep learning is responsible for today’s explosion of AI. It has given computers extraordinary powers, like the ability to recognize spoken words almost as well as a person could, a skill too complex to code into the machine by hand. Deep learning has transformed computer vision and dramatically improved machine translation. It is now being used to guide all sorts of key decisions in medicine, finance, manufacturing—and beyond.

但直到本世纪初，经过几次巧妙的调整和改进，非常大或“深”的神经网络在自动感知方面才表现出了巨大的进步。深度学习是今天人工智能爆炸的原因。它给计算机带来了非凡的力量，如几乎能像人那样识别口语的能力，这项技术太复杂以至于无法用手工编码到机器中。深度学习变革了计算机视觉，极大地改进了机器翻译。它现在被用来指导医学、金融、制造业以及其它领域的各种关键决策。

The workings of any machine-learning technology are inherently more opaque, even to computer scientists, than a hand-coded system. This is not to say that all future AI techniques will be equally unknowable. But by its nature, deep learning is a particularly dark black box.

任何机器学习技术的运转本质上都比手工编码系统要难懂得多，甚至对计算机科学家来说也是如此。这并不是说未来所有的人工智能技术都将同样不可知。但就其性质而言，深度学习是一个特别隐秘的黑盒。

You can’t just look inside a deep neural network to see how it works. A network’s reasoning is embedded in the behavior of thousands of simulated neurons, arranged into dozens or even hundreds of intricately interconnected layers. The neurons in the first layer each receive an input, like the intensity of a pixel in an image, and then perform a calculation before outputting a new signal. These outputs are fed, in a complex web, to the neurons in the next layer, and so on, until an overall output is produced. Plus, there is a process known as back-propagation that tweaks the calculations of individual neurons in a way that lets the network learn to produce a desired output.

你不能仅仅看一个深度神经网络就了解到它是如何工作的。一个网络的推理被嵌入在数千个模拟神经元的行为中，这些神经元排列在几十个甚至数百个错综复杂的相连层中。第一层中的每个神经元接收一个输入，如图像中像素的强度，然后执行计算输出一个新信号。在一个复杂的网络中，这些输出被送到下一层的神经元中，如此往复，直到产生最后的输出。另外，还有一个被称为反向传播的过程，它通过调整单个神经元的计算使网络学习产生期望输出。

The many layers in a deep network enable it to recognize things at different levels of abstraction. In a system designed to recognize dogs, for instance, the lower layers recognize simple things like outlines or color; higher layers recognize more complex stuff like fur or eyes; and the topmost layer identifies it all as a dog. The same approach can be applied, roughly speaking, to other inputs that lead a machine to teach itself: the sounds that make up words in speech, the letters and words that create sentences in text, or the steering-wheel movements required for driving.

深度网络中的多层使它能够在不同抽象层上识别事物。例如，在一个识别狗的系统中，较低层识别轮廓或颜色等简单的事物；较高层识别皮毛或眼睛等更复杂的东西；而最上层则将其视为一只狗。大致来说，同样的方法也可以应用于其它引导机器自学的输入中：如形成演讲中话的声音，生成文本中句子的字母和单词，或驾驶所需的方向盘运动。

**“It might be part of the nature of intelligence that only part of it is exposed to rational explanation. Some of it is just instinctual.”**

**“这可能是智力天性的一部分，其中只有一部分智力暴露在理性解释之下。而有些仅仅只是本能。”**

Ingenious strategies have been used to try to capture and thus explain in more detail what’s happening in such systems. In 2015, researchers at Google modified a deep-learning-based image recognition algorithm so that instead of spotting objects in photos, it would generate or modify them. By effectively running the algorithm in reverse, they could discover the features the program uses to recognize, say, a bird or building. The resulting images, produced by a project known as Deep Dream, showed grotesque, alien-like animals emerging from clouds and plants, and hallucinatory pagodas blooming across forests and mountain ranges. The images proved that deep learning need not be entirely inscrutable; they revealed that the algorithms home in on familiar visual features like a bird’s beak or feathers. But the images also hinted at how different deep learning is from human perception, in that it might make something out of an artifact that we would know to ignore. Google researchers noted that when its algorithm generated images of a dumbbell, it also generated a human arm holding it. The machine had concluded that an arm was part of the thing.

巧妙的策略被用来试图捕捉并更详细地解释这种系统中正在发生的事情。2015年，谷歌研究员修改了一种基于深度学习的图像识别算法，它将生成或修改照片中的对象，而不是发现它们。通过有效地逆向运行该算法，他们可以发现程序用来识别如一只鸟或建筑物的特征。相应的由Deep Dream项目产生的图像，展示了从云彩和植物中出现的怪诞的，像外星人一样的动物，以及绽放在森林和山脉中致幻的宝塔。图像表明，深度学习不一定是完全神秘莫测的；他们发现算法指向熟悉的视觉特征，如鸟的喙或羽毛。但这些图像也暗示了深度学习与人类感知有多么不同，因为它可能会产生某些超出我们人工制品外的东西，在这些人工制品中我们可能会忽视这些东西。谷歌研究员注意到，当算法生成一个哑铃的图像时，它也产生了一个手臂。机器断定手臂是物体的一部分。

Further progress has been made using ideas borrowed from neuroscience and cognitive science. A team led by Jeff Clune, an assistant professor at the University of Wyoming, has employed the AI equivalent of optical illusions to test deep neural networks. In 2015, Clune’s group showed how certain images could fool such a network into perceiving things that aren’t there, because the images exploit the low-level patterns the system searches for. One of Clune’s collaborators, Jason Yosinski, also built a tool that acts like a probe stuck into a brain. His tool targets any neuron in the middle of the network and searches for the image that activates it the most. The images that turn up are abstract (imagine an impressionistic take on a flamingo or a school bus), highlighting the mysterious nature of the machine’s perceptual abilities.

使用神经科学和认知科学的想法我们取得了进一步的进展。University of Wyoming助理教授Jeff Clune领导的团队，采用与光学错觉等价的AI测试了深度神经网络。2015年，Clune团队表明某些图像可以愚弄这样一个网络感知本不存在的事物，因为图像滥用了系统搜索的低级模式。Clune的一位合作者，Jason Yosinski，还构建了一个工具，它就像一根插入大脑的探针一样。他的工具瞄准网络中间的任何一个神经元，并搜索最能激活它的图像。而这样的图像是抽象的（想象一个火烈鸟或校车的写意照），它突出了机器感知能力的神秘性。

We need more than a glimpse of AI’s thinking, however, and there is no easy solution. It is the interplay of calculations inside a deep neural network that is crucial to higher-level pattern recognition and complex decision-making, but those calculations are a quagmire of mathematical functions and variables. “If you had a very small neural network, you might be able to understand it,” Jaakkola says. “But once it becomes very large, and it has thousands of units per layer and maybe hundreds of layers, then it becomes quite un-understandable.”

然而，我们需要更多地了解AI的想法，没有简单的解决方案。深度神经网络中计算的相互影响对高级模式识别和复杂决策至关重要，但那些计算是一些复杂的数学函数和变量。Jaakkola说：“如果你有一个很小的神经网络，你可以理解它。但一旦它变得非常大，每层有上千个单元，可能有上百个层，那它就变得不可理解了。”

In the office next to Jaakkola is Regina Barzilay, an MIT professor who is determined to apply machine learning to medicine. She was diagnosed with breast cancer a couple of years ago, at age 43. The diagnosis was shocking in itself, but Barzilay was also dismayed that cutting-edge statistical and machine-learning methods were not being used to help with oncological research or to guide patient treatment. She says AI has huge potential to revolutionize medicine, but realizing that potential will mean going beyond just medical records. She envisions using more of the raw data that she says is currently underutilized: “imaging data, pathology data, all this information.”

麻省理工教授Regina Barzilay在Jaakkola隔壁办公室，她正将机器学习应用于医学。几年前，在她43岁时，她被诊断出患有乳腺癌。诊断本身是令人震惊的，但Barzilay也很沮丧，尖端的统计和机器学习方法还未被用来帮助肿瘤研究或指导患者治疗。她说，人工智能在医学变革方面有巨大的潜力，但意识到这一潜力将意味着超越单纯的医疗记录。她希望使用更多的原始数据，她说这些原始数据目前还未充分利用：“图像数据、病理数据，所有这些信息。”

**How well can we get along with machines that are unpredictable and inscrutable?**

**我们如何与不可预测、神秘莫测的机器相处？**


After she finished cancer treatment last year, Barzilay and her students began working with doctors at Massachusetts General Hospital to develop a system capable of mining pathology reports to identify patients with specific clinical characteristics that researchers might want to study. However, Barzilay understood that the system would need to explain its reasoning. So, together with Jaakkola and a student, she added a step: the system extracts and highlights snippets of text that are representative of a pattern it has discovered. Barzilay and her students are also developing a deep-learning algorithm capable of finding early signs of breast cancer in mammogram images, and they aim to give this system some ability to explain its reasoning, too. “You really need to have a loop where the machine and the human collaborate,” -Barzilay says.

去年完成癌症治疗后，Barzilay和她的学生们就开始与马萨诸塞州总医院的医生们合作开发了一个能够挖掘病理报告来确定患者的具体临床特征的系统，研究者可能会对这些特征进一步研究。然而，Barzilay明白，系统需要解释其原因。所以，她跟Jaakkola以及一个学生一起，增加了一步：系统提取并突出代表它发现的模式的文本片段。Barzilay和她的学生也正在开发一种能够在乳腺X线图像中发现早期乳腺癌症状的深度学习算法，她们的目标是也赋予系统一些解释其推理的能力。Barzilay说：“你真的需要有一个机器与人类协作的循环。”

The U.S. military is pouring billions into projects that will use machine learning to pilot vehicles and aircraft, identify targets, and help analysts sift through huge piles of intelligence data. Here more than anywhere else, even more than in medicine, there is little room for algorithmic mystery, and the Department of Defense has identified explainability as a key stumbling block.

美国军方正投入数十亿美元在那些利用机器学习引导车辆和飞机，确定目标，帮助分析人员筛选大量情报数据的项目中。这里比其它任何地方都多，甚至超过了在医学上，几乎没有算法神秘性的空间，美国国防部认为可解释性是一个关键的绊脚石。

David Gunning, a program manager at the Defense Advanced Research Projects Agency, is overseeing the aptly named Explainable Artificial Intelligence program. A silver-haired veteran of the agency who previously oversaw the DARPA project that eventually led to the creation of Siri, Gunning says automation is creeping into countless areas of the military. Intelligence analysts are testing machine learning as a way of identifying patterns in vast amounts of surveillance data. Many autonomous ground vehicles and aircraft are being developed and tested. But soldiers probably won’t feel comfortable in a robotic tank that doesn’t explain itself to them, and analysts will be reluctant to act on information without some reasoning. “It’s often the nature of these machine-learning systems that they produce a lot of false alarms, so an intel analyst really needs extra help to understand why a recommendation was made,” Gunning says.

美国国防高级研究计划署的项目经理David Gunning，负责Explainable Artificial Intelligence项目。作为该机构曾负责监督DARPA项目（最终促成了Siri的产生）的一位银发老兵，Gunning说自动化正在逐渐蔓延到不计其数的军事领域。情报分析员正在测试机器学习，以此来识别大量监视数据中的模式。许多自动地面车辆和飞机正在研制和试验中。但士兵们可能在一个无法解释自己的机器人坦克中无法感到舒适，分析师也不愿奉行没有原因的信息。Gunning说：“产生大量的误报通常是这些机器学习系统的本质，所以英特尔分析师确实需要额外的帮助才能理解为什么会有这样的建议。”

This March, DARPA chose 13 projects from academia and industry for funding under Gunning’s program. Some of them could build on work led by Carlos Guestrin, a professor at the University of Washington. He and his colleagues have developed a way for machine-learning systems to provide a rationale for their outputs. Essentially, under this method a computer automatically finds a few examples from a data set and serves them up in a short explanation. A system designed to classify an e-mail message as coming from a terrorist, for example, might use many millions of messages in its training and decision-making. But using the Washington team’s approach, it could highlight certain keywords found in a message. Guestrin’s group has also devised ways for image recognition systems to hint at their reasoning by highlighting the parts of an image that were most significant.

今年3月，DARPA选择了来自学术界和工业界的13个项目，在Gunning的计划下资助。它们中的一些构建在华盛顿大学教授Carlos Guestrin领导的工作上。他和他的同事已经开发出机器学习系统中为输出提供理论基础的一种方法。本质上，在这种方法下，计算机自动从一个数据集中找到几个示例，并为它们提供一个简短的解释。例如，一个被设计用于将电子邮件分类成来自恐怖分子的系统，可能会在其训练和决策过程中使用数百万条信息。但使用华盛顿团队的方法，它可以突出消息中发现的某些关键词。Guestrin团队还为图像识别系统设计了通过突出图像最重要的部分来暗示推理的方法。

One drawback to this approach and others like it, such as Barzilay’s, is that the explanations provided will always be simplified, meaning some vital information may be lost along the way. “We haven’t achieved the whole dream, which is where AI has a conversation with you, and it is able to explain,” says Guestrin. “We’re a long way from having truly interpretable AI.”

这种方法以及其它类似方法（如Barzilay的方法）的一个缺点是给出的解释总是过于简单，这意味着一些重要的信息可能会丢失。Guestrin说：“我们还没有实现全部的梦想，那时AI可以与你交谈，它也能解释，我们离真正可解释的人工智能还有很长的路要走。”

It doesn’t have to be a high-stakes situation like cancer diagnosis or military maneuvers for this to become an issue. Knowing AI’s reasoning is also going to be crucial if the technology is to become a common and useful part of our daily lives. Tom Gruber, who leads the Siri team at Apple, says explainability is a key consideration for his team as it tries to make Siri a smarter and more capable virtual assistant. Gruber wouldn’t discuss specific plans for Siri’s future, but it’s easy to imagine that if you receive a restaurant recommendation from Siri, you’ll want to know what the reasoning was. Ruslan Salakhutdinov, director of AI research at Apple and an associate professor at Carnegie Mellon University, sees explainability as the core of the evolving relationship between humans and intelligent machines. “It’s going to introduce trust,” he says.

它不一定是像癌症诊断或军事演习这样的高风险情况，这成了一个问题。如果技术将成为我们日常生活中一个常见有用的部分，那么了解AI的推理也将是至关重要的。在苹果公司领导Siri的Tom Gruber，称可解释性是他团队的一个关键考虑，因为它试图让Siri成为一个更聪明更强大的虚拟助手。Gruber不愿讨论Siri未来的具体计划，但很容易想象，如果你收到一个来自Siri的餐馆推荐，你会想知道原因是什么。苹果人工智能研究室主任、卡内基梅隆大学副教授Ruslan Salakhutdinov，将可解释性视为人与智能机器之间进化关系的核心。他说：“这将引入信任。”

Just as many aspects of human behavior are impossible to explain in detail, perhaps it won’t be possible for AI to explain everything it does. “Even if somebody can give you a reasonable-sounding explanation [for his or her actions], it probably is incomplete, and the same could very well be true for AI,” says Clune, of the University of Wyoming. “It might just be part of the nature of intelligence that only part of it is exposed to rational explanation. Some of it is just instinctual, or subconscious, or inscrutable.”

正如人类行为的许多方面都无法详细解释一样，也许人工智能无法解释它所做的每一件事。怀俄明大学的Clune说：“即使有人能[对他或她的动作]给你一个看似合理的解释，它可能是不完整的，这同样适用于AI，这可能只是智力天性的一部分，其中只有一部分暴露在理性解释之下。有些仅仅是本能的，或潜意识的，或神秘莫测的。”

If that’s so, then at some stage we may have to simply trust AI’s judgment or do without using it. Likewise, that judgment will have to incorporate social intelligence. Just as society is built upon a contract of expected behavior, we will need to design AI systems to respect and fit with our social norms. If we are to create robot tanks and other killing machines, it is important that their decision-making be consistent with our ethical judgments.

如果是这样的话，那么在某个阶段，我们可能不得不简单地相信AI的判断或者不使用它。同样，这种判断也必须纳入社会智能。正如社会是建立在预期行为的契约之上一样，我们需要设计人工智能系统来尊重和适应我们的社会规范。如果我们要创造机器人坦克和其它杀人机器，重要的是它们的决策要符合我们的道德判断。

To probe these metaphysical concepts, I went to Tufts University to meet with Daniel Dennett, a renowned philosopher and cognitive scientist who studies consciousness and the mind. A chapter of Dennett’s latest book, From Bacteria to Bach and Back, an encyclopedic treatise on consciousness, suggests that a natural part of the evolution of intelligence itself is the creation of systems capable of performing tasks their creators do not know how to do. “The question is, what accommodations do we have to make to do this wisely—what standards do we demand of them, and of ourselves?” he tells me in his cluttered office on the university’s idyllic campus.

为了探讨这些形而上的概念，我去Tufts University见了著名的哲学家和认知科学家Daniel Dennett，他研究意识和智力。Dennett新书【From Bacteria to Bach and Back】（这是一本关于意识的百科全书式的论述）的一章，认为智力本身进化的一部分特性是创造能够执行它们的创造者都不知道怎么做的任务的系统。他在坐落于田园诗般的校园中他杂乱的办公室里告诉我：“问题是，我们要做哪些调节适应才能明智地去做这些事？我们要求它们和我们自己的标准是什么？”。

He also has a word of warning about the quest for explainability. “I think by all means if we’re going to use these things and rely on them, then let’s get as firm a grip on how and why they’re giving us the answers as possible,” he says. But since there may be no perfect answer, we should be as cautious of AI explanations as we are of each other’s—no matter how clever a machine seems. “If it can’t do better than us at explaining what it’s doing,” he says, “then don’t trust it.”

他也有一句关于追寻可解释性的警告。他说：“我认为，如果我们打算使用这些东西，并依赖它们，那么我们就牢牢地把握它们如何以及为什么会给我们这些答案了”。但由于可能没有完美的答案，我们应该尽可能谨慎地对待AI的可解释性--不管机器看上去有多聪明。他说：“如果它在解释做什么方面不如我们，那么不要相信它。”

