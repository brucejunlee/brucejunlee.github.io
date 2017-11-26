---
layout: post
title: "[SIAM NEWS] Nonlinear Ocean-Wave Interactions on Flat Beaches"
author: "李军"
categories: journal
tags: [siam, soliton]
image:
  feature: 
  teaser: 
  credit: 
  creditlink: ""
---

By <u>M.J. Ablowitz</u> and D.E. Baldwin

June 03, 2013

[M.J. Ablowitz is a professor of applied mathematics at the University of Colorado, Boulder, from which D.E. Baldwin recently received a PhD.]

People have always been fascinated by waves, particularly water and ocean waves. The mathematical study of water waves goes back to the origins of differential equations. While linear equations are often good models for small-amplitude waves, nonlinear equations are needed for larger amplitudes. We have seen and photographed interacting nonlinear waves that occur daily at two relatively flat beaches; a well-known nonlinear wave equation has solutions that are remarkably similar to what we observed

人们总是被海浪吸引，尤其是水和海浪。水波的数学研究可以追溯到微分方程的起源。虽然线性方程通常是小振幅波的良好模型，但更大振幅需要非线性方程组。我们看到并拍摄了每天在两个相对平坦的海滩上相互作用的非线性波；著名的非线性波动方程的解与我们观察到的非常相似。

Even Newton (1642-1727) was interested in providing a mathematical description of water waves, but many years would pass before this was feasible. In 1757 Euler derived the inviscid equations of fluid dynamics. Soon afterward, Laplace and Lagrange found linear approximations to the water-wave equations. In 1816 Cauchy’s study of the linear initial-value problem of water waves won a prize from the French Academy of Sciences. This work, an early application of Fourier analysis, was not well understood at the time. But in general, water-wave dynamics satisfy nonlinear equations because the wave amplitudes are not sufficiently small.

甚至牛顿（1642-1727）是提供水波的数学描述感兴趣，但许多年过去后，这是可行的。1757欧拉导出流体动力学的无粘方程。不久之后，Laplace和拉格朗日发现了水波方程的线性近似。1816，柯西对水波线性初值问题的研究获法国科学院奖。这项工作是傅立叶分析的早期应用，当时还不是很清楚。但一般情况下，由于波浪振幅不够小，水波动力学满足非线性方程组。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-oceanwave-1.jpg)

Figure 1. Short-stem X-type interaction; see also [2]. (a) Contour plot of an analytical line-soliton interaction solution of the KP equation (here $e^Φ$ ≈ 2:3)). (b) Photograph taken in Mexico, December 31, 2011. (c) 3D plot of the solution shown in (a).

In 1847, Stokes derived the correct nonlinear boundary conditions on the water’s free surface and used it to show that the speed of a traveling wave in deep water depends on its amplitude. In the 1870s, understanding that the nonlinear water-wave equations are simplified when the water is shallow or the waves are long, Boussinesq derived (1+1)-dimensional equations (one space and one time dimension); he found a solitary wave solution that is localized and nonperiodic. In 1895 Korteweg and his student de Vries followed Boussinesq’s pioneering path and derived a unidirectional (1+1)-dimensional nonlinear equation for shallow water, usually called the Korteweg–de Vries (KdV) equation. They also found special periodic solutions, which they called cnoidal waves, that can be written in terms of Jacobian elliptic functions. The cnoidal wave, in a special limit, becomes a solitary wave. A solitary wave had been observed in 1834 by Russell, a naval engineer; he found that the wave’s speed depends on its amplitude, which agrees with the KdV equation’s solitary wave.

1847，斯托克斯在水的自由面上推导出了正确的非线性边界条件，并用它证明了深水中行波的速度取决于它的振幅。在19世纪70年代，了解非线性水波方程进行了简化，当水浅、浪长，Boussinesq源（1 + 1）维方程（一个空间和一维时间）；他发现了孤立波解是局部的和非周期的。1895度和他的学生de Vries跟随Boussinesq的创业路径和导出单向（1 + 1）-浅水非线性方程，通常称为KdV–de Vries（KdV）方程。他们还发现了特殊的周期解，他们称之为椭圆余弦波，可以用Jacobi椭圆函数。椭圆余弦波，在一个特殊的限制，成为一个孤立波。一位海军工程师罗素在1834观察到一个孤立波，他发现波的速度取决于它的振幅，这与KdV方程的孤立波一致。

Between 1895 and 1960, most applications of the KdV equation involved water waves. But in the 1960s mathematicians found that the KdV equation is universal: It arises in wave problems with weak dispersion and weak quadratic nonlinearity. Besides water waves, the KdV equation arises in stratified fluids, plasma physics, elasticity, and lattice dynamics, among other settings. It was lattice dynamics that motivated Kruskal and Zabusky in 1965 to carry out a numerical study of the KdV equation. They discovered that these KdV solitary waves have special interaction properties: Their amplitudes before and after interaction are preserved, but there is a phase shift. They called these special solitary waves solitons. Soon afterward, in 1967, Gardner, Greene, Kruskal, and Miura developed a method—later named the inverse scattering transform (IST) method—for finding the solution. They also found a spectral interpretation for solitons. Their work spurred great interest, and many researchers made important contributions.

在1895到1960年间，KdV方程的大多数应用都涉及水波。但在20世纪60年代，数学家们发现KdV方程是普遍存在的：它是在弱色散和弱二次非线性波问题中产生的。除了水波外，KdV方程还包括分层流体、等离子体物理、弹性和晶格动力学等。这是晶格动力学激励秩和Zabusky 1965开展了KdV方程的数值研究。他们发现，这些孤立波具有特殊的相互作用性质：它们的相互作用前后振幅保持不变，但存在相移。他们称这些孤立波为孤立波。不久，1967，加德纳，格林尼，和，和缪拉开发的方法后来被命名为反散射变换（IST）求解方法。他们还发现了孤子的光谱解释。他们的工作引起了极大的兴趣，许多研究者作出了重要贡献。

Equations solvable with the IST method, like the KdV equation, are often called integrable. In 1970 Kadomtsev and Petviashvili (KP) found a multidimensional (two-space, one-time) generalization of the KdV equation; it is also integrable and can be derived from the water-wave equations in shallow water with surface tension included. Like the KdV equation, it has soliton solutions that can be written explicitly. The simplest is a plane-wave solution, which is essentially one-dimensional and satisfies the KdV equation.

用IST方法求解的方程，如KdV方程，通常称为可积方程。1970的Petviashvili（KP）发现了一个多维（两空间，一次性）KdV方程的推广；也可积，可得到表面张力在浅水波方程包括水。像KdV方程一样，它有可以明确写出的孤子解。最简单的是平面波解，它基本上是一维的，满足KdV方程。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-oceanwave-2.jpg)

Figure 2. Contour plot (a) and photographs (b), (c) of a Y-type interaction ($e^Φ$ = 0); see also [2]. (b) Taken in Mexico, January 6, 2010. (c) Taken in California, May 3, 2012.

The well-known two-soliton solutions, first found in the 1970s, are more interesting; surprisingly, similar interactions are visible on a daily basis on relatively flat beaches. It is useful to write the two-soliton solution of the KP equation, with small surface tension, with a phase-shift parameter that we label $e^ϕ$. We concentrate on four cases: $e^ϕ$ order one, $e^ϕ$ large, $e^ϕ$ zero, and $e^ϕ$ small. Remarkably, we have seen each of these types at the beach; we call them short-stem X-, long-stem X-, Y-, and H-type interactions, respectively.

著名的两孤子解，最早出现在20世纪70年代，更有趣；令人惊讶的是，每天在相对平坦的海滩上都能看到类似的相互作用。这是写了KP方程的双孤子解有用，表面张力较小，与相移参数，我们标记E ^ϕ美元美元。我们专注于四种情况：a ^ϕ为一美元，美元ϕE ^美元美元大，E ^ϕ零美元，美元和美元^ϕ小E。值得注意的是，我们所看到的每一种类型的海滩；我们称之为短干X，长茎的X，Y，和H型的相互作用，分别。

Before our recent observations, there was only one known photograph—of a long-stem X-type interaction, taken on the Oregon coast in the 1970s (see [1], page 291). MJA saw and photographed short- and long-stem X-type and Y-type interactions in Nuevo Vallarta, Mexico; he also occasionally saw and photographed more complex multisoliton interactions. Motivated by this and the KP equation’s analytic solutions, DEB traveled to Venice Beach, California, where he saw and photographed not only interactions of the types seen by MJA, but also H-type interactions. We observed these soliton interactions daily on relatively flat beaches, in shallow water, within about two hours of low tide. Being near a jetty helps the development of cross-waves but is not necessary if there is a good crosswind. We have seen mainly two-soliton interactions but occasionally have spotted more complex soliton interactions as well. Additional details and photos can be found in our paper [2], and we have also posted [photos](http://www.douglasbaldwin.com/nl-waves.html) and videos on our websites.

在我们最近的观察，只有一个已知的照片一长杆型的互动，在俄勒冈海岸，在上世纪70年代（见[ 1 ]，291页）。MJA看到并拍下短和长柄的X型和Y型相互作用的新塔，墨西哥；他也偶尔看到和拍到更复杂的多孤子相互作用。受此启发和KP方程的解析解，Deb前往威尼斯海滩，加利福尼亚，在那里他看到和拍到的不仅是被MJA型相互作用，而且H型的相互作用。我们每天在相对平坦的海滩上，在浅水中观察到这些孤子相互作用，大约在低潮两小时左右。在接近码头有助于跨波的发展但不必要的如果有一个好的侧风。我们主要看到了两个孤子相互作用，但偶尔也发现了更复杂的孤子相互作用。额外的细节和照片可以在文[ 2 ]，我们也贴[组图](http://www.douglasbaldwin.com/nl-waves.html)和我们网站上的视频。

Along with the phase shift, some of these distinctive nonlinear interactions are explained in part by the stem height: Not just the sum of the wave heights away from the interaction, it can be considerably higher. This can be important in descriptions of tsunami propagation, which in certain cases can be modeled with the KP equation. Indeed, satellite images reveal local X- and Y-type interactions for the 2011 Japanese earthquake-induced tsunami. This made the effects of the tsunami even worse. Because the Japanese tsunami was close to shore, nonlinearity did not have time to amplify the stem height; other tsunamis might occur well away from shore, in which case nonlinear effects could become important. In such cases X- and Y-type tsunami interactions could be extremely destructive.

随着相位的变化，这些独特的非线性相互作用部分是由茎的高度来解释的：不只是远离相互作用的波高之和，它可以相当高。这在海啸传播的描述中很重要，在某些情况下可以用KP方程来描述。事实上，卫星图像显示X和Y相互作用的局部为2011日本大地震引起的海啸。这使海啸的影响更严重。由于日本海啸接近海岸，非线性没有时间来放大茎的高度；其他海啸可能会发生远离海岸，在这种情况下，非线性效应可能成为重要的。在这种情况下，X和Y的相互作用可能是极具破坏性的海啸。

**References**

[1] M.J. Ablowitz and H. Segur, Solitons and the Inverse Scattering Transform, SIAM, Philadelphia, 1981.

[2] M.J. Ablowitz and D.E. Baldwin, Nonlinear shallow ocean-wave soliton interactions on flat beaches, Phys. Rev. E, 86 (2012), 036305.