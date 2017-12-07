---
layout: post
title: "[SIAM NEWS] From Global to Local: Getting More from Compressed Sensing"
author: "李军"
categories: journal
tags: [siam, compressed sensing]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

By Alexander Bastounis, Ben Adcock, and <u>Anders C. Hansen</u>

October 02, 2017

[Alexander Bastounis is a final-year Ph.D. student in the Applied Functional and Harmonic Analysis group in the Department of Applied Mathematics and Theoretical Physics at the University of Cambridge. His research interests include compressed sensing, optimisation theory, computability theory, and applied functional analysis. Ben Adcock is an assistant professor at Simon Fraser University. He received the Leslie Fox Prize for Numerical Analysis in 2011, an Alfred P. Sloan Research Fellowship in 2015, and the CAIMS-PIMS Early Career Award in 2017. His research interests include applied and computational harmonic analysis, numerical analysis, and approximation theory. Anders C. Hansen is the head of the Applied Functional and Harmonic Analysis group at the University of Cambridge, where he is a reader (associate professor) in mathematics. He is also a Royal Society University Research Fellow. His research interests are include computational harmonic analysis, foundations of computational mathematics, mathematical signal processing, functional analysis, numerical analysis, and mathematical physics.]

---

Over the last decade, compressed sensing and sparse recovery techniques have had a significant impact on applied mathematics and its uses in science and engineering. Compressed sensing applications have moved beyond experimentation and are beginning to be seen in new implementations. An area of particular note is imaging, where compressed sensing can be used in magnetic resonance imaging (MRI), electron tomography, and radio interferometry, among other applications. With this in mind, it is timely to revisit the mathematics of compressed sensing as it pertains to imaging. While the standard theory of compressed sensing is justifiably celebrated, it falls somewhat short of explaining phenomena that result from the application of these techniques to imaging. In this article, we describe recent work that seeks to bridge this gap. As we demonstrate, our approach yields significant practical benefits in imaging, allowing researchers to further push the limits of performance.

在过去十年中，压缩感知和稀疏恢复技术对应用数学及其在科学和工程中的应用产生了重大影响。压缩感知应用已经超越了实验，并开始出现在新的实现中。特别值得注意的一个领域是成像，这里压缩感知可用于核磁共振（magnetic resonance imaging，MRI）、电子层析成像、无线电干涉测量以及其它应用中。考虑到这一点，重温压缩感知的数学是适时的，因为它涉及到成像。虽然压缩感知的标准理论是值得庆祝的，但在解释这些技术在图像方面应用时产生的现象仍有不足。在这篇文章中，我们描述了最近试图弥合这一差距的工作。正如我们所展示的，我们的方法在成像方面产生了显著的实际效益，使研究者能够进一步推动性能极限。

**Standard Compressed Sensing**

**标准压缩感知**

Compressed sensing [3, 4, 6] concerns the recovery of an object from an incomplete set of linear measurements. In a discrete setting, one can formulate this as the linear system

压缩感知 [3, 4, 6] 涉及从一组不完全的线性测量中恢复对象的问题。在离散情况中，人们可以把它描述成线性系统

$$y=Ax$$,

where y∈ℂ<sup>m</sup> is the vector of measurements, x∈ℂ<sup>N</sup> is the object to recover, and A∈ℂ<sup>m×N</sup> is the so-called measurement matrix. In practice, the number of measurements m is often substantially smaller than the dimension N, making recovery generally impossible. To overcome this, compressed sensing leverages two key properties: sparsity of the vector x and incoherence of the measurement vectors (rows of A). The first property asserts that x should have at most s≤m significant components, with the remaining components relatively small, while the second states that the measurement vectors should be (in a formally-defined sense) spread out, rather than concentrated around a small number of entries.

这里，y∈ℂ<sup>m</sup>是测量向量，x∈ℂ<sup>N</sup>是要恢复的对象，A∈ℂ<sup>m×N</sup>是所谓的测量矩阵。实践过程中，测量数m通常比维数N小得多，这使得通常不能恢复。为了克服这种情况，压缩感知利用两个关键性质：向量x的稀疏性以及测量向量（A的行）的不相干。第一个性质要求x至多有s≤m个重要分量，剩下的分量相对很小，而第二个性质要求测量向量应该（在正式定义的角度看）分散而不是集中在一小块元素周围。

A popular tool in compressed sensing theory is the Restricted Isometry Property (RIP). A matrix has the RIP or order s if there exists a δ∈(0,1), such that 

在压缩感知理论中的一种常用工具是受限等距性质（Restricted Isometry Property，RIP）。如果存在一个δ∈（0,1），使得对于所有s-稀疏的向量x，都有

$$(1−δ)‖x‖^2_{ℓ^2}≤‖Ax‖^2_{ℓ^2}≤(1+δ)‖x‖^2_{ℓ^2}$$, for all s-sparse vectors x.

那么矩阵就具有RIP性质或者s阶。

For instance, if recovery is performed by solving the convex basis pursuit problem

例如，如果通过求解凸基追踪问题

$$min_{z∈ℂ^N} ‖z‖_{ℓ^1}$$, subject to $$Az=y$$,(1)

来进行恢复过程

then the RIP (with sufficiently small δ) implies exact recovery of any s-sparse x and robustness with respect to perturbations in x (i.e., inexact sparsity) or y (i.e., noise).

那么RIP（δ足够小）意味着任何s-稀疏的向量x都能精确恢复，对于x（即不精确的稀疏）或y（即噪声）的扰动也是健壮的。

Typically, the rows of A are drawn independently according to some random distribution. An elegant demonstration of compressed sensing mathematics considers Gaussian random vectors. These are incoherent, and a signature result asserts that A has the RIP with an optimal number of measurements m≈Cslog(N/s).

通常，A的行是根据一些随机分布独立抽取的。压缩感知的一个简明表达考虑高斯随机向量。这些向量都是不相干的，结果表明A具有RIP性质，且最优测量数为m≈Cslog(N/s)。

**The Flip Test**

**翻转实验**

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-cs-globallocal-1.jpg)

Figure 1. The flip test. 1a. Radial sampling map in k-space. White pixels denote the frequencies sampled. 1b. Image x̂, recovered using Haar wavelets (PSNR = 28.7dB). 1c. Flipped recovery x̌ (PSNR = 15dB). 1d. Flipped recovery where the flipping is done in levels (PSNR = 29.0dB). Image credit: Alexander Bastounis, Ben Adcock, and Anders C. Hansen.

Imaging is an ideal fit for compressed sensing, and one of its original areas of application [5, 8, 11]. Though not typically sparse themselves, images can be represented sparsely in certain dictionaries, such as wavelets. Furthermore, acquisition devices found in many imaging applications are modelled with the Fourier transform, which tends to be fairly incoherent.

成像非常适合于压缩感知，而且也是它最初的应用领域之一[5, 8, 11]。虽然图像本身并不稀疏，但它可以在小波等字典中稀疏表示。此外，在许多成像应用中发现的图像获取设备都是用傅立叶变换来建模的，这往往相当不相干。

In their seminal work [3], Emmanuel Candès, Justin Romberg, and Terence Tao demonstrated the benefits of compressed sensing by recovering the classical Shepp-Logan phantom from incomplete Fourier measurements. This experiment is repeated in Figures 1a-1c. The theoretical basis for this result is twofold. First, the image x∈ℂ<sup>N</sup> has a sparse representation in a wavelet basis. Specifically, if Φ∈ℂ<sup>N×N</sup> is the matrix of the wavelet transform, then

Emmanuel Candès，Justin Romberg和Terence Tao在他们的开创性工作[3]中，通过从不完全傅立叶测量中恢复经典的Shepp-Logan幽灵来证明压缩感知的好处。该实验在图1a-1c中被重复。这一结果的理论基础分两部分。首先，图像x∈ℂ<sup>N</sup>在小波基上有一个稀疏表示。具体来说，如果Φ∈ℂ<sup>N×N</sup>是小波变换矩阵，那么对于一些s-稀疏的系数向量c∈ℂ<sup>N</sup>有

$$x=Φc$$

for some s-sparse vector of coefficients c∈ℂ<sup>N</sup>. Second, the matrix 

其次，矩阵

$$A=PFΦ$$(2)

has the RIP, where F∈ℂ<sup>N×N</sup> is the discrete Fourier matrix and P∈ℂ<sup>m×N</sup> is the matrix of the sampling map, i.e., P selects rows of F according to frequencies shown in Figure 1b. As per the theory, x should recover to high accuracy as x̂ =Φĉ, where ĉ is a solution of (1).

有RIP性质，这里F∈ℂ<sup>N×N</sup>是离散傅立叶矩阵，P∈ℂ<sup>m×N</sup>是采样映射矩阵，即P根据图1b所示的频率来选择F的行。根据理论，x应该恢复到高精度x̂ =Φĉ，其中ĉ是（1）的一个解。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-cs-globallocal-2.jpg)

Figure 2. Asymptotic sparsity and asymptotic incoherence. 2a. Wavelet coefficients of the Shepp-Logan phantom, arranged according to increasing scale. 2b. Coefficients of the flipped phantom. 2c. Radial sampling map in k-space. The square annulus regions denote the essential frequency concentration of wavelets at a given scale. 2d. Absolute values of the matrix U=FΦ, with larger and smaller values corresponding to lighter or darker colours respectively. Vertical lines indicate the wavelet scales and horizontal lines indicate the annular frequency bands. Image credit: Alexander Bastounis, Ben Adcock, and Anders C. Hansen.

To examine the extent to which this theory explains the results observed in Figure 1, we perform the following experiment, known as the flip test [1]. Let Q∈ℂ<sup>N×N</sup> be a permutation matrix and define the permuted coefficients c<sub>p</sub>=Qc and corresponding image <sub>p</sub>=Φc<sub>p</sub>. Now let ĉ<sub>p</sub> be the coefficients recovered by solving (1) with y=PFx<sub>p</sub>, and define č=Q<sup>−1</sup>ĉ<sub>p</sub> and x̌=Φč. Since permutations do not affect sparsity, coefficients c<sub>p</sub> are s-sparse and image x<sub>p</sub> has an s-sparse representation in the wavelet basis. Hence, if matrix A has the RIP, one would expect both the unflipped reconstruction x̂ and flipped reconstruction x̌ to yield similar recoveries of the original image x.

为了检查这一理论对图1观察到的结果的解释程度，我们进行了以下实验，即翻转测试[1]。让Q∈ℂ<sup>N×N</sup>表示一个置换矩阵，定义置换系数c<sub>p</sub>=Qc以及相应的图像x<sub>p</sub>=Φc<sub>p</sub>。现在让ĉ<sub>p</sub>表示通过求解（1）（其中y=PFx<sub>p</sub>）恢复的系数，同时定义č=Q<sup>−1</sup>ĉ<sub>p</sub>和x̌=Φč。由于置换不影响稀疏性，系数c<sub>p</sub>是s-稀疏的，且图像x<sub>p</sub>在小波基上有一个s-稀疏表示。因此，如果矩阵A有RIP性质，人们希望未翻转的重构x̂和翻转重构x̌都要产生原始图像x的相似恢复。

Figure 1d demonstrates that this is not the case. The flipped reconstruction—in this example, the permutation simply reverses the ordering of the coefficients—is significantly worse than the unflipped reconstruction. We therefore conclude that the RIP cannot hold. Additionally, since certain sparse vectors are recovered better than others, distribution of the wavelet coefficients is crucial to recovery.

图1d表明情况并非如此。翻转重构（在这个例子中，置换只是将系数简单地逆序）要比未翻转重构差得多。因此，我们推断它并不没有RIP性质。此外，由于某些稀疏向量要比其它稀疏向量恢复得好，所以小波系数的分布对恢复至关重要。

Classical wavelet theory can intuitively explain these results. As illustrated in Figure 2a, wavelet coefficients, when arranged according to dyadic scales, are sparser at finer scales than coarser scales. Moreover, wavelets at a given scale are essentially concentrated in square annular regions of k-space (see Figure 2c). The radial sampling pattern samples less densely in regions corresponding to the fine scales, where the image is more sparse, and more densely at coarse scales, where the image is less sparse. However, if the coefficients are permuted (see Figure 2b), too many coefficients exist at fine scales (compared to the number of high-frequency samples) to ensure good recovery.

经典的小波理论可以直观地解释这些结果。如图2a，当按二进制尺度排列时，小波系数在细尺度上要比粗尺度上更稀疏。此外，在一个给定的尺度上的小波基本上都集中在k-空间的方环区域（图2c）。径向采样模式在与细尺度对应的区域内采样更少，图像更稀疏，而在粗尺度区域采样更密集，图像不太稀疏。然而，如果系数被置换（见图2b），那么在细尺度下存在太多系数（相较于高频样本数）以至于不能保证良好的恢复。

**A Levels-based Framework**

**一个基于层级的框架**

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-cs-globallocal-3.jpg)

Figure 3. Compressed sensing using 6.25% Fourier measurements at various resolutions. Original image courtesy of Andy Ellison, recovered images by Alexander Bastounis, Ben Adcock, and Anders C. Hansen.

To provide a more comprehensive compressed sensing framework, the approach in [1, 2] first replaces the global concepts of sparsity and incoherence with suitable local quantities. Specifically, let r be a number of levels and **M**=(M<sub>1</sub>,…,M<sub>r</sub>), where 1≤M<sub>1</sub>\<…\<M<sub>r</sub>=N, a vector of sparsity levels. These may typically correspond to wavelet scales. Rather than a single sparsity index s, the new model considers a vector **s**=(s<sub>1</sub>,…,s<sub>r</sub>) of local sparsities, with s<sub>k</sub> as the sparsity at the kth level. We refer to vector x∈ℂ<sup>N</sup> with this sparsity pattern as (**s**, **M**)-sparse in levels.

为给出一个更综合的压缩感知框架，[1, 2]中的方法首先用合适的局部量来代替全局的稀疏性和不相干的概念。具体来说，让r表示大量层级，**M**=(M<sub>1</sub>,…,M<sub>r</sub>)表示一个稀疏层级向量，这里1≤M<sub>1</sub>\<…\<M<sub>r</sub>=N。这些通常对应于小波尺度。新模型考虑了局部稀疏的向量**s**=(s<sub>1</sub>,…,s<sub>r</sub>)而不是单一的稀疏索引s，这里s<sub>k</sub>表示第k层的稀疏性。我们称含有这个稀疏模式的向量x∈ℂ<sup>N</sup>是层级上（**s**, **M**）-稀疏的。

Note that permutations performed in Figure 2c destroy sparsity in levels but not global sparsity. Conversely, Figure 2d demonstrates that permutations within scales do not unduly alter the reconstruction quality, thus demonstrating the appropriateness of the （**s**, **M**）-sparsity model. 

注意，在图2c中进行的置换破坏了层级上的稀疏性但并没有破坏全局稀疏性。相反，图2d演示了尺度内的置换不会过度改变重构质量，从而证明了（**s**, **M**）-稀疏模型的适当性。

A modified version of the RIP helps analyze recovery with this model [2]. Matrix A has the RIP in levels (RIPL) of order （**s**, **M**） if there exists a δ∈(0,1), such that

RIP性质的一个修正版有助于用这个模型来分析恢复[2]。如果存在一个δ∈（0,1），使得对于所有的（**s**, **M**）-稀疏的向量x，都满足

$$(1−δ)‖x‖^2_{ℓ^2}≤‖Ax‖^2_{ℓ^2}≤(1+δ)‖x‖^2_{ℓ^2}$$, for all（**s**, **M**）-sparse vectors x.

那么矩阵A在阶为（**s**, **M**）的层上有RIP性质（RIPL）。

Much like the standard RIP, if A has the RIPL (for small δ<sub>s,M</sub>), then all （**s**, **M**）-sparse vectors can be robustly recovered by solving (1).

就像标准的RIP，如果A有RIPL（对于小δ<sub>s,M</sub>），那么所有的（**s**, **M**）-稀疏向量都可以通过求解（1）来强健恢复。

Returning to Fourier sampling with wavelet sparsity, this novel sparsity model calls for a new type of sampling, known as multilevel random subsampling. The idea is to break up the rows of the matrix U into levels [1], following the block-diagonal structure illustrated in Figure 2d. Specifically, we introduce sampling levels N=(N<sub>1</sub>,…,N<sub>r</sub>), where 1≤N<sub>1</sub>\<…\<N<sub>r</sub>=N, and a vector m=(m<sub>1</sub>,…,m<sub>r</sub>) of local numbers of measurements. Within each sampling level, m<sub>k</sub> samples are chosen uniformly at random. Using this approach, one can show that the matrix (2) satisfies the RIPL (in the one-dimensional setting) [7], provided

回到具有小波稀疏性的傅立叶采样，这种新颖的稀疏模型要求一种新的采样方法，即多级随机子采样。这个想法是要把矩阵U拆散成层级[1]，就是如图2d所示的块对角结构。具体来说，我们引入采样层级**N**=(N<sub>1</sub>,…,N<sub>r</sub>), 这里 1≤N<sub>1</sub>\<…\<N<sub>r</sub>=N, 和局部测量数的向量**m**=(m<sub>1</sub>,…,m<sub>r</sub>)。在每一采样层，随机均匀地选择m<sub>k</sub>个样本。使用这种方法，给定

$$m_k \approx C \left(s_k + \sum^r_{l=1,j \neq k} 2^{−\vert l−k \vert}s_l \right) log^3(N) log^2(s)$$, k=1,…,r.(3)

人们能显示矩阵（2）满足RIPL性质（在一维情况下）[7]。
 
That is, the number of measurements m<sub>k</sub> required to capture each wavelet scale should be roughly proportional to the corresponding sparsity s<sub>k</sub>.

也就是说，需要捕获每一小波尺度所需的测量数m<sub>k</sub>应该大致与相应的稀疏性s<sub>k</sub>成比例。

**Applications and Benefits**

**应用和好处**

By refining the sparsity model and sampling procedure, this framework not only explains the observations of the flip test but also significantly enhances compressed sensing performance in various imaging settings. By following sparsity patterns of the wavelet coefficients, one can exploit (3) to develop sampling patterns that target the sparsity in levels structure and thereby enhance reconstruction quality.

通过细化稀疏模型和采样过程，该框架不仅解释了翻转测试的观测结果，而且在各种成像环境下也显著提高了压缩感知的性能。通过追踪小波系数的稀疏模式，人们可以利用（3）开发出针对层次结构稀疏性的采样模式，从而提高重构质量。

We conclude by demonstrating these benefits in several practical settings (see [10] for further experiments). First, Figure 3 compares the recovery of a magnetic resonance image at various resolutions from Fourier measurements, taken according to radial and multilevel sampling patterns. Multilevel sampling is consistently superior to radial sampling because it better targets the image’s sparsity structure. This benefit also increases with the resolution, since the multilevel sampling pattern aligns increasingly well with the wavelet coefficients’ asymptotic sparsity.

最后，我们在几个实际环境中展示了这些优点（更多实验见[10]）。首先，图3比较了根据径向采样模式和多级采样模式得到的傅立叶测量中各种分辨率下的核磁共振图像的恢复情况。多级采样始终优于径向采样，因为它更好地针对图像的稀疏结构。这种好处也随着分辨率的增加而增加，因为多级采样模式与小波系数的渐近稀疏性越来越吻合。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-cs-globallocal-4.jpg)

Figure 4. Resolution enhancing in MRI. 4a. Original image with small synthetic detail added. 4b. Linear recovery from the lowest m=256<sup>2</sup> Fourier measurements. 4c. Compressed sensing with multilevel subsampling using m=256<sup>2</sup> measurements. Original image courtesy of Andy Ellison, recovered images by Alexander Bastounis, Ben Adcock, and Anders C. Hansen.

From this latter observation we conclude the following: instead of using compressed sensing at lower resolutions to reduce acquisition time, one can best realize the full benefits by subsampling at higher resolutions and seeking to improve image quality. In other words, compressed sensing is most beneficial as a resolution enhancer. Figure 4 demonstrates this effect. For a fixed budget of measurements, subsampling from higher resolutions yields a vastly superior reconstruction when compared to full sampling at low frequencies. Both Siemens—a leading manufacturer of MRI scanners [13]—and [10] further verify this phenomenon in a practical MRI setting.

从后者的观察来看，我们得出以下结论：人们通过在高分辨率下子采样、寻求改善图像质量实现了全部好处，而非在低分辨率下使用压缩感知来减少采集时间。换句话说，压缩感知最有利于提高分辨率。图4展示了这种效果。对于一个固定的测量预算，相比在低频处完全采样，从高分辨率中子采样产生了非常好的重构。Siemens（一家行业领先的MRI扫描仪生成商[13]）和[10]都在实际的成像环境中进一步验证了这一现象。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-cs-globallocal-5.jpg)

Figure 5. Compressive imaging. 5a. Original image. 5b. Recovery from m=16.5% scrambled Hadamard measurements. 5c. Recovery from m=16.5% multilevel subsampled Hadamard measurements. Image credit: Alexander Bastounis, Ben Adcock, and Anders C. Hansen.

Finally, Figure 5 considers a class of problems informally known as compressive imaging [11]. In these problems—the applications of which include single-pixel [5] and lensless imaging, infrared imaging, and fluorescence microscopy [12]—one can choose the measurement matrix A, provided that its entries are binary. In this case, a randomly-subsampled Hadamard transform with scrambled columns is a standard choice for A. This is a computationally-efficient procedure whose performance mimics that of random Gaussian sampling; it is near-optimal for recovering sparse vectors. It may therefore seem surprising that the reconstruction quality can be improved. However, as Figure 5 shows, a multilevel subsampled Hadamard transform (without column scrambling) does precisely this. Even though wavelet coefficients are sparse, the procedure targets the image’s fine details (captured by the fine-scale wavelet coefficients) to achieve a significant performance gain.

最后，图5考虑了一类被称为压缩成像的问题[11]。在这些问题中（包括单像素[5]和无透镜成像、红外成像以及荧光显微等应用），已知元素是二值的，人们可以选择测量矩阵A。在这种情况下，随机子采样得到的列是扰乱的Hadamard变换是A的一个标准选择。这是一个计算上高效的过程，它的性能可以比拟随机高斯采样，这对于恢复稀疏向量是近似最优的。因此，可以提高重构质量看上去也很惊奇。然而，如图5所示，一个多级子采样Hadamard变换（列没有被扰乱）可以精确完成。即使小波系数是稀疏的，这一过程仍然对准图像的细节（通过细尺度小波系数来获取）从而实现了显著的性能增益。


**Acknowledgments:** The authors thank Andy Ellison for the MR images used in Figures 3 and 4.

**Other resources:**

[The Dark Side of Image Reconstruction](https://sinews.siam.org/Details-Page/the-dark-side-of-image-reconstruction-1)

[See Light Move: Compressed Sensing and the World’s Fastest 2-D Camera](https://sinews.siam.org/Details-Page/see-light-move-compressed-sensing-and-the-worlds-fastest-2-d-camera)

**References**

[1] Adcock, B., Hansen, A.C., Poon, C., & Roman, B. (2017). Breaking the coherence barrier: A new theory for compressed sensing. Forum of Mathematics, Sigma, 5.

[2] Bastounis, A., & Hansen, A.C. (2017). On the absence of uniform recovery in many real-world applications of compressed sensing and the restricted isometry property and nullspace property in levels. SIAM J. Imaging Sci., 10(1), 335-371.

[3] Candès, E.J., Romberg, J., & Tao, T. (2006). Robust uncertainty principles: exact signal reconstruction from highly incomplete frequency information. IEEE Trans. Inform. Theory, 52(2), 489-509.

[4] Donoho, D.L. (2006). Compressed sensing. IEEE Trans. Inform. Theory, 52(4), 1289-1306.

[5] Duarte, M.F., Davenport, M.A., Takhar, D., Laska, J., Kelly, K., & Baraniuk, R.G. (2008). Single-pixel imaging via compressive sampling. IEEE Signal Process. Mag., 25(2), 83-91.

[6] Foucart, S., & Rauhut, H. (2013). A Mathematical Introduction to Compressive Sensing: Applied and Numerical Harmonic Analysis. New York, NY: Birkhauser.

[7] Li, C., & Adcock, B. (2017). Compressed sensing with local structure: uniform recovery guarantees for the sparsity in levels class. Appl. Comput. Harmon. Anal. (to appear). arXiv:1601.01988.

[8] Lustig, M., Donoho, D.L., Santos, J.M., & Pauly, J.M. (2008). Compressed Sensing MRI. IEEE Signal Process. Mag., 25(2), 72-82.

[9] Poon, C. (2015). On the role of total variation in compressed sensing. SIAM J. Imaging Sci., 8(1), 682-720. 

[10] Roman, B., Calderbank, R., Adcock, B., Nietlispach, D., Bostock, M., Calvo-Almazán, I., Graves, M., & Hansen, A.C. (2017). Undersampling improves fidelity of physical imaging and the benefits grow with resolution. Preprint.

[11] Romberg, J. (2008). Imaging via compressive sampling. IEEE Signal Process. Mag., 25(2), 14-20.

[12] Studer, V., Bobin, J., Chahid, M., Moussavi, H., Candès, E., & Dahan, M. (2011). Compressive fluorescence microscopy for biological and hyperspectral imaging. Proc. Natl Acad. Sci., 109(26), 1679-1687.

[13] Wang, Q., Zenge, M., Cetingul, H.E., Mueller, E., & Nadar, M.S. (2014). Novel sampling strategies for sparse MR image reconstruction. Proc. Int. Soc. Mag. Res. in Med., 22.