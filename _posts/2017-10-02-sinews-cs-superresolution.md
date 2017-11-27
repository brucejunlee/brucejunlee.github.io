---
layout: post
title: "[SIAM NEWS] Super-resolution and Compressed Sensing"
author: "李军"
categories: journal
tags: [siam, compressed sensing]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

By <u>Carlos Fernandez-Granda</u>

October 01, 2013

[Carlos Fernandez-Granda is a Ph.D. student in the Department of Electrical Engineering at Stanford University.]

It has long been known that a lens, however perfect, has limited resolving power.

人们早就知道，不管镜头多么完美，分辨率都很有限。 

As Lord Rayleigh pointed out in his seminal 1891 paper “On Pin-hole Photography,” diffraction imposes an inflexible limit on the resolution of any optical system. As a result, in such fields as microscopy, astronomy, and medical imaging, it is often challenging to discern cellular structures, far-away galaxies, or incipient tumours from the available data. Super-resolution aims to meet precisely that challenge—to uncover fine-scale structure from coarse-scale measurements. This problem also arises in electronic imaging, where photon shot noise constrains the minimum possible pixel size, and in many other applications, including signal processing, spectroscopy, radar, and seismology.

正如Lord Rayleigh在其开创性的1891篇关于针孔摄影的论文中指出的，衍射对任何光学系统的分辨率都有一个严格的限制。因此，在显微镜、天文学和医学成像等领域，从现有的数据中分辨出细胞结构、遥远的星系或早期肿瘤常常是具有挑战性的。超分辨率正是为了迎接这一挑战，从粗尺度测量中发现精细尺度结构。这个问题也出现在电子成像中，其中光子散粒噪声限制了最小可能的像素大小，在许多其他应用中，包括信号处理、光谱学、雷达和地震学。

In its most general formulation, the problem of super-resolution is ill posed. This becomes apparent in the frequency domain. Low-resolution measurements essentially erase the high end of the spectrum; consequently, we cannot hope to retrieve the missing fine-scale information without prior knowledge of our object of interest. Under one popular assumption, we can model the signal as a superposition of point sources or spikes, which might represent celestial bodies in astronomy, molecules in fluorescence microscopy, or line spectra in signal processing. Figure 1 illustrates the resulting inverse problem: The aim is to estimate the train of spikes at the upper left from the blurry measurements at the upper right or, equivalently, to extrapolate the high frequencies at the lower left from the truncated spectrum at the lower right. Under what conditions can we hope to achieve this? The answer must surely involve exploiting the sparsity of the signal, which suggests connections with compressed sensing.

在最一般的公式中，超分辨率的问题是不适定的。这在频域中变得明显。低分辨率的测量基本上消除了光谱的高端，因此，我们不可能在没有事先了解我们感兴趣的对象的情况下检索丢失的精细尺度信息。在一个流行的假设下，我们可以将信号建模为点源或尖峰的叠加，这可能代表天文学中的天体，荧光显微镜中的分子，或信号处理中的线谱。图1演示了产生的逆问题：其目的是估计右上角模糊测量左上角的尖峰，或者等价地推断右下角截断频谱左下角的高频。我们希望在什么条件下做到这一点？答案肯定包括利用信号的稀疏性，这表明与压缩感知有关。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-cs-superresolution-1.jpg)
 
Figure 1. Schematic illustration of the super-resolution problem. Left, a highly resolved signal and its spectrum. Right, low-pass measurements of the signal and the corresponding truncated spectrum.

In a nutshell, compressed sensing allows the recovery of a low-dimensional structure embedded in a high-dimensional space. Surprisingly, this is achieved by taking non-adaptive randomized measurements and solving a tractable convex program. When applied to our model of interest, compressed-sensing theory guarantees that we can reconstruct any sequence of k spikes from approximately Ck random Fourier coefficients by solving the ℓ<sub>1</sub>-norm minimization problem

简而言之，压缩感知允许恢复高维空间中的低维结构。令人惊讶的是，这是通过采取非自适应随机测量和解决一个听话的凸程序来实现的。当应用到我们的利益的模式，压缩感知理论的保证，我们可以从傅里叶系数约为对照的随机解决ℓ<子> 1 <子> -范数最小化问题重建序列的K尖峰

$$min_x ||x||_{ℓ_1}$$

among all signals x consistent with the data. Moreover, the recovery scheme can be stable in the presence of noise. This is possible because the random-sensing operator is well conditioned when its domain is restricted to the class of sparse signals. Intuitively, such a condition is necessary for recovery by any method in a realistic setting; otherwise, the signal could be completely lost in the measurement process.

在所有信号中x与数据一致。此外，在噪声存在的情况下，恢复方案是稳定的。这是可能的，因为随机感测算子在其域仅限于稀疏信号类时被很好地调节。直观地说，这样的条件是必要的恢复在现实环境中的任何方法，否则，信号可以完全丧失在测量过程中。

Returning to the problem of super-resolution: As a first step, we should investigate whether the low-pass operator is well conditioned when acting on sparse signals. This does not follow at all from compressed-sensing theory, which ensures that it is possible to interpolate the spectrum of a sparse signal from random samples, but says nothing about extrapolating the higher end of the spectrum from low-frequency samples. The second row of Figure 2 illustrates the difference between the two measurement schemes: In both cases we subsample in the frequency domain, but compressed sensing gives us access to the entire spectrum, whereas in super-resolution we are restricted to the low-pass frequencies. It turns out that low-pass filtering of sparse signals, unlike randomized spectral sampling, can be very badly conditioned. A simple example helps make this important point. The signal in the left column of Figure 2 is very sparse, but the fraction of its energy located in the lower quarter of its spectrum is only about $10^{–8}$! No recovery scheme—no matter how sophisticated—could possibly estimate this signal from low-pass measurements in the presence of even the slightest perturbation. In sharp contrast, if the whole spectrum is sampled at random, the measurements do capture a sizable fraction of the energy of the signal. Indeed, compressed sensing recovers the highly clustered signal from a quarter of its discrete spectrum, as shown at the lower left in Figure 2.

回到超分辨率问题：作为第一步，我们应该研究低通算子在稀疏信号作用下是否有良好的条件。这完全不是压缩传感理论所遵循的，它保证从随机样本中提取稀疏信号的频谱是可能的，但对从低频样本中推断出更高的频谱端没有任何意义。图2的第二行说明了这两种测量方法之间的区别：在这两种情况下，我们的子样本在频率域，但压缩传感给我们访问整个频谱，而在超分辨率是限制我们的低通频率。事实证明，稀疏信号的低通滤波不同于随机光谱采样，它可以非常恶劣地被限制。一个简单的例子有助于阐明这一点。图2左栏中的信号非常稀疏，但其能量位于其谱的下半部分的部分仅约为10美元8美元！无论多么复杂的恢复方案都不可能在低信号的情况下估计这个信号，即使有轻微的扰动。与此形成鲜明对比的是，如果整个频谱是随机取样的，那么测量就捕获了信号能量的一个相当大的部分。事实上，压缩感知从其离散频谱的四分之一恢复高度聚集的信号，如图2所示的左下角所示。

A careful reader might wonder whether the example on the left of Figure 2 is pathological, in the sense that the spectrum of most sparse signals might not be as concentrated in the high frequencies. We can do a simple experiment to test whether this is so. Consider the vectors of length 5000 that end in 4950 zeros. This defines a vector space of dimension 50 composed entirely of very sparse signals, to which we apply a low-pass filter retaining a quarter of the spectrum. Taking the singular value decomposition of the filter restricted to this vector space reveals that a subspace S of dimension 22 is almost completely destroyed; the fraction of the remaining energy for any signal in S is at most 10<sup>–10</sup>! This phenomenon was characterized theoretically by Slepian in the 1970s. His work on prolate spheroidal sequences confirms that, asymptotically, most tightly clustered sparse signals are almost completely annihilated by low-pass filtering.

细心的读者可能会怀疑图2左边的例子是否是病态的，在这个意义上，大多数稀疏信号的频谱可能不象高频那样集中。我们可以做一个简单的实验来测试它是否是这样的。考虑长度为5000的向量，其结尾为4950个零。这定义了一个完全由非常稀疏的信号组成的维数50的向量空间，我们应用一个低通滤波器保留了四分之一的频谱。仅限于该向量空间的滤波器的奇异值分解表明维数22的子空间S几乎完全被破坏，s中任何信号的剩余能量的分数至多为10×10！这种现象的特点从理论上讲，在上世纪70年代Slepian。他对椭球的工作证实，渐近，最密集的稀疏信号几乎全军覆没的低通滤波。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-cs-superresolution-2.jpg)
 
Figure 2. Compressed sensing recovers any sparse signal, even highly clustered ones, from random spectral samples. Super-resolution via ℓ<sub>1</sub>-norm minimization extrapolates the high frequencies of sparse signals that are not too clustered.

Does this mean that super-resolution of sparse signals is completely hopeless? Not if we are willing to add some further structure to our model. We must impose conditions on the support of the signal to preclude its being too clustered. The right column of Figure 2 shows a signal that is identical to the one in the left column, except that its support is more spread out. Spacing out the spikes results in a spectrum that is not as concentrated in the higher frequencies. For such signals super-resolution from low-pass measurements is no longer hopeless. In fact, as shown at the lower right in the figure, ℓ<sub>1</sub>-norm minimization succeeds in reconstructing the signal exactly from the lower quarter of its spectrum.

这是否意味着稀疏信号的超分辨率是完全没有希望的？如果我们愿意在模型中添加更多的结构，就不行了。我们必须在信号的支持上施加条件，防止信号过于集中。图2的右栏显示的信号与左栏中的信号相同，只是它的支持更分散。间距的尖峰导致频谱不集中在更高的频率。对于这种信号，低通测量的超分辨率不再是无望的。事实上，在图中的右下所示，ℓ<子> 1 <子>范数最小化成功重构信号的频谱是从下季度。

The outcome of this example is encouraging, but is it typical? The answer is yes. Recent work has established that ℓ<sub>1</sub>-norm minimization super-resolves any train of spikes as long as the separation between spikes is at least 2/f<sub>c</sub>, where f<sub>c</sub> denotes the cut-off frequency of the measurements. Exact recovery is guaranteed even in a gridless setting, where the spikes may be supported at arbitrary points of a continuous interval. In that case, the recovery algorithm can be recast as a discrete semidefinite program, which locates the support of the signal with infinite precision. Furthermore, the method is provably robust to perturbations and can be adapted to signals of other types, such as piecewise-smooth functions.

这个例子的结果是令人鼓舞的，但它是典型的吗？答案是肯定的。最近的工作已经确定，ℓ<子> 1 <子> -范数最小化的超级解决任何列车尖峰只要尖峰之间的分离至少是2 / f＜子＞C＜/子>，<子> < f c /子>表示截止频率的测量。精确恢复甚至在无网格设定，在尖峰可能在一个连续区间任意点支承。在这种情况下，恢复算法可以转化为一个离散半定规划，它以无限的精度定位信号的支持。此外，该方法对扰动具有较强的鲁棒性，适用于其它类型的信号，如分段光滑函数。 

To recapitulate, sparsity is not enough to characterize the problem of super-resolution. Refining the signal model to exclude highly clustered signals not only ensures that the problem is well posed in principle, it is actually sufficient to guarantee the success of a tractable method based on convex optimization. This illustrates a central theme in modern signal processing: Understanding the interaction between the sensing process and certain low-dimensional structures—such as sparse vectors or low-rank matrices—allows us to develop non-parametric algorithms that are remarkably successful at extracting information from high-dimensional data.

概括的说，稀疏不足以表征超分辨率问题。改进信号模型以排除高度聚集的信号不仅保证了问题在原则上是良好的，实际上也足以保证基于凸优化的易于处理的方法的成功。这说明了现代信号处理中的一个中心主题：理解传感过程与某些低维结构（如稀疏向量或低秩矩阵）之间的相互作用，使我们能够开发出从高维数据中提取信息非常成功的非参数算法。

**Acknowledgments:** The author is grateful to Gilbert Strang for encouraging him to write this article and to his adviser, Emmanuel Candès, for his support.

**Related Publication:** E.J. Candès and C. Fernandez-Granda, Towards a mathematical theory of super-resolution. Comm. Pure Appl. Math., to appear.