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

正如1891年Lord Rayleigh在其开创性论文“On Pin-hole Photography”中指出，衍射对任何光学系统的分辨率都有一个严格的限制。因此，在显微镜、天文学和医学成像等领域中，从现有数据中分辨出细胞结构、遥远星系或早期肿瘤常常是极具挑战性的。超分辨率正是为了应对这一挑战，从粗尺度测量中发现细尺度结构。这个问题也出现在电子成像（这里光子散粒噪声限制了最小可能的像素大小）和许多其他应用（包括信号处理、光谱学、雷达和地震学等）中。

In its most general formulation, the problem of super-resolution is ill posed. This becomes apparent in the frequency domain. Low-resolution measurements essentially erase the high end of the spectrum; consequently, we cannot hope to retrieve the missing fine-scale information without prior knowledge of our object of interest. Under one popular assumption, we can model the signal as a superposition of point sources or spikes, which might represent celestial bodies in astronomy, molecules in fluorescence microscopy, or line spectra in signal processing. Figure 1 illustrates the resulting inverse problem: The aim is to estimate the train of spikes at the upper left from the blurry measurements at the upper right or, equivalently, to extrapolate the high frequencies at the lower left from the truncated spectrum at the lower right. Under what conditions can we hope to achieve this? The answer must surely involve exploiting the sparsity of the signal, which suggests connections with compressed sensing.

在最一般的形式中，超分辨率问题是病态的。这在频域中非常明显。低分辨率测量本质上消除了光谱的高端，因此，我们不可能在没有我们感兴趣对象的先验知识的情况下恢复丢失的细尺度信息。在一个流行的假设下，我们可以将信号建模成点源或尖峰的叠加，这或许可以表示天文学中的天体、荧光显微镜中的分子或信号处理中的线谱等。图1说明了相应的反问题：其目的是估计右上角模糊测量中左上角的一系列尖峰，或等价地推断右下角截断频谱中左下角的高频。我们希望在什么条件下做到这一点呢？答案肯定包括运用信号的稀疏性，这表明与压缩感知有关。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-cs-superresolution-1.jpg)
 
Figure 1. Schematic illustration of the super-resolution problem. Left, a highly resolved signal and its spectrum. Right, low-pass measurements of the signal and the corresponding truncated spectrum.

In a nutshell, compressed sensing allows the recovery of a low-dimensional structure embedded in a high-dimensional space. Surprisingly, this is achieved by taking non-adaptive randomized measurements and solving a tractable convex program. When applied to our model of interest, compressed-sensing theory guarantees that we can reconstruct any sequence of k spikes from approximately Ck random Fourier coefficients by solving the ℓ<sub>1</sub>-norm minimization problem

简单来讲，压缩感知可以从高维空间中恢复低维结构。令人惊讶的是，这是通过先进行非自适应随机测量然后求解一个易处理的凸规划来实现的。当运用到我们的有趣模型时，压缩感知理论保证了我们可以通过求解ℓ<sub>1</sub>范数最小化问题

$$min_x ||x||_{ℓ_1}$$

among all signals x consistent with the data. Moreover, the recovery scheme can be stable in the presence of noise. This is possible because the random-sensing operator is well conditioned when its domain is restricted to the class of sparse signals. Intuitively, such a condition is necessary for recovery by any method in a realistic setting; otherwise, the signal could be completely lost in the measurement process.

从所有与数据一致的信号x中大约Ck个随机傅里叶系数中重建任意K尖峰序列。此外，恢复方案在有噪声情况下也是很稳定的。这是可能的，因为受限于稀疏信号类时随机感知算子适应得很好。直观地说，这样的恢复条件在现实环境的任何方法中都是必要得，否则信号在测量过程中可能完全丢失。

Returning to the problem of super-resolution: As a first step, we should investigate whether the low-pass operator is well conditioned when acting on sparse signals. This does not follow at all from compressed-sensing theory, which ensures that it is possible to interpolate the spectrum of a sparse signal from random samples, but says nothing about extrapolating the higher end of the spectrum from low-frequency samples. The second row of Figure 2 illustrates the difference between the two measurement schemes: In both cases we subsample in the frequency domain, but compressed sensing gives us access to the entire spectrum, whereas in super-resolution we are restricted to the low-pass frequencies. It turns out that low-pass filtering of sparse signals, unlike randomized spectral sampling, can be very badly conditioned. A simple example helps make this important point. The signal in the left column of Figure 2 is very sparse, but the fraction of its energy located in the lower quarter of its spectrum is only about 10<sup>–8</sup>! No recovery scheme—no matter how sophisticated—could possibly estimate this signal from low-pass measurements in the presence of even the slightest perturbation. In sharp contrast, if the whole spectrum is sampled at random, the measurements do capture a sizable fraction of the energy of the signal. Indeed, compressed sensing recovers the highly clustered signal from a quarter of its discrete spectrum, as shown at the lower left in Figure 2.

回到超分辨率问题：第一步，我们应该研究在作用于稀疏信号时低通算子是否适应得很好。这完全不是压缩感知理论所遵循的，因为压缩感知理论保证了插值随机样本中的稀疏信号谱是可能的，但对于从低频样本中推断出高端频谱没有任何说明。图2第二行举例说明了两种测量方法之间的差别：在这两种情况下，我们都在频域进行子采样，但压缩感知使我们可以访问整个频谱，然而在超分辨率问题中我们限制在低通频率。事实证明，不同于随机谱采样，稀疏信号的低通滤波可能适应得非常差。一个简单的例子有助于阐明这一点。图2左列的信号非常稀疏，但位于低区域谱的能量占比大概仅有10<sup>–8</sup>！无论多成熟的恢复方案都不能从低通测量中估计这个信号，即使扰动微乎其微。与此对比鲜明的是，如果随机采样整个频谱，那么测量就可以捕获一大部分信号能量。事实上，压缩感知可以从一部分离散频谱中恢复高度集聚的信号，如图2左下角所示。

A careful reader might wonder whether the example on the left of Figure 2 is pathological, in the sense that the spectrum of most sparse signals might not be as concentrated in the high frequencies. We can do a simple experiment to test whether this is so. Consider the vectors of length 5000 that end in 4950 zeros. This defines a vector space of dimension 50 composed entirely of very sparse signals, to which we apply a low-pass filter retaining a quarter of the spectrum. Taking the singular value decomposition of the filter restricted to this vector space reveals that a subspace S of dimension 22 is almost completely destroyed; the fraction of the remaining energy for any signal in S is at most 10<sup>–10</sup>! This phenomenon was characterized theoretically by Slepian in the 1970s. His work on prolate spheroidal sequences confirms that, asymptotically, most tightly clustered sparse signals are almost completely annihilated by low-pass filtering.

细心的读者可能会怀疑图2左边的例子是否是病态的，在这方面来说，大多数稀疏信号谱可能并没有集中在高频区域。我们可以做一个简单的实验来测试一下是否真是如此。考虑末尾有4950个零的长度为5000的向量。这定义了一个完全由极其稀疏的信号组成的50维向量空间，我们在该空间中应用了一个只保留一小部分频谱的低通滤波。对仅限于该向量空间的滤波进行奇异值分解表明一个22维的子空间S几乎完全被消除了，空间S中任何信号的剩余能量部分至多10<sup>–10</sup>！这一现象在上世纪70年代就在理论上被Slepian描述了。他对椭球序列的工作证实，紧密聚集的稀疏信号几乎完全被低通滤波湮灭了。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-cs-superresolution-2.jpg)
 
Figure 2. Compressed sensing recovers any sparse signal, even highly clustered ones, from random spectral samples. Super-resolution via ℓ<sub>1</sub>-norm minimization extrapolates the high frequencies of sparse signals that are not too clustered.

Does this mean that super-resolution of sparse signals is completely hopeless? Not if we are willing to add some further structure to our model. We must impose conditions on the support of the signal to preclude its being too clustered. The right column of Figure 2 shows a signal that is identical to the one in the left column, except that its support is more spread out. Spacing out the spikes results in a spectrum that is not as concentrated in the higher frequencies. For such signals super-resolution from low-pass measurements is no longer hopeless. In fact, as shown at the lower right in the figure, ℓ<sub>1</sub>-norm minimization succeeds in reconstructing the signal exactly from the lower quarter of its spectrum.

这是否意味着稀疏信号的超分辨率是完全无用的呢？如果我们在模型中再添加一些结构，那就真不行了。我们必须在信号支持上强加条件以防止信号过于集聚。图2右列展示了一个与左列相同的信号，只是它的支持更分散。将尖峰排开使得频谱不太集中在高频区域。对于这种信号，从低通测量中进行超分辨率操作将不再是无用的。事实上，如图中右下角所示，ℓ<sub>1</sub>范数最小化成功从低区域频谱中精确重构出了信号。

The outcome of this example is encouraging, but is it typical? The answer is yes. Recent work has established that ℓ<sub>1</sub>-norm minimization super-resolves any train of spikes as long as the separation between spikes is at least 2/f<sub>c</sub>, where f<sub>c</sub> denotes the cut-off frequency of the measurements. Exact recovery is guaranteed even in a gridless setting, where the spikes may be supported at arbitrary points of a continuous interval. In that case, the recovery algorithm can be recast as a discrete semidefinite program, which locates the support of the signal with infinite precision. Furthermore, the method is provably robust to perturbations and can be adapted to signals of other types, such as piecewise-smooth functions.

这个例子的结果是令人鼓舞的，但它是典型的吗？答案是肯定的。最近的工作已经确定，只要尖峰间的间隔至少为2/f<sub>c</sub>（这里f<sub>c</sub>表示测量的截止频率），那么ℓ<sub>1</sub>范数最小化就能够对任何尖峰序列进行超分辨率操作。精确恢复甚至在无网格情况下也能保证，这里尖峰可能在一个连续区间的任意点处。在那种情况下，恢复算法可以转化成一个离散半定规划问题，它以无限精度来设定信号支持。此外，该方法对扰动具有较强的鲁棒性，同时也适用于其它类型的信号，如分段光滑函数。 

To recapitulate, sparsity is not enough to characterize the problem of super-resolution. Refining the signal model to exclude highly clustered signals not only ensures that the problem is well posed in principle, it is actually sufficient to guarantee the success of a tractable method based on convex optimization. This illustrates a central theme in modern signal processing: Understanding the interaction between the sensing process and certain low-dimensional structures—such as sparse vectors or low-rank matrices—allows us to develop non-parametric algorithms that are remarkably successful at extracting information from high-dimensional data.

概括一下，稀疏不足以表征超分辨率问题。改进信号模型以排除高度聚集的信号，不仅保证了问题在原则上是适定的，实际上也足以保证基于凸优化的易处理方法的成功。这说明了现代信号处理的一个中心主题：对感知过程与某些低维结构（如稀疏向量或低秩矩阵）之间的相互作用的理解，使得我们能够开发出非参算法，该算法在抽取高维数据中的信息方面非常成功。

**Acknowledgments:** The author is grateful to Gilbert Strang for encouraging him to write this article and to his adviser, Emmanuel Candès, for his support.

**Related Publication:** E.J. Candès and C. Fernandez-Granda, Towards a mathematical theory of super-resolution. Comm. Pure Appl. Math., to appear.