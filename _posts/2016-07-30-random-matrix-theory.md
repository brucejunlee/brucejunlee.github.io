---
layout: post
title: "随机矩阵理论(一): 综述"
author: "李军"
categories: journal
tags: [RMT]
image:
  feature: 
  teaser: 
  credit: 
  creditlink: ""
---

随机矩阵理论自一开始就注重理论联系实际，随着时间发展已经深入到很多学科领域，如随机过程，PDE，数论，统计，图论，医药，生物，神经科学，金融，信号处理，无线通信，甚至机器学习，深度学习等计算机科学中。因此，我们很难毫无疏漏地把RMT讲述清楚。下面，我将RMT分成几个不同部分来写，不定期地推出。本文是随机矩阵理论系列的第一篇文章，主要描述一些产生背景，发展过程和几个重要的定理定律及其证明方法。

#### 什么是[随机矩阵](https://en.wikipedia.org/wiki/Random_matrix)

A random matrix is a matrix-valued random variable—that is, a matrix some or all of whose elements are random variables.

Or see Persi Diaconis(2005), <u>What is ... a random matrix?</u>

#### 预备知识

+ 矩阵论
+ 微积分
+ 概率论

#### 简史
+ 史前：Fisher，PL Hsu，Wishart，Von Neumann，LK Hua
+ 创世[1950s]：E. Wigner
+ 第一阶段[1950s-1980s]：Dyson，Marcenko-Pastur，Erdos-Renyi，M Mehta，Muirhead
+ 第二阶段[late 1980s]：Nick Trefethen，Alan Edelman，Tracy-Widom，Zhidong Bai，[Smale(1985)]，Silverstein，Peter Forrester，Persi Diaconis
+ 第三阶段[2000s-]：Terence Tao，Donoho，Percy Deift，Tropp，HorngTzer Yau，Vu，Raj Rao Nadakuditi，Dimitris Achlioptas，Couillet，Robert Qiu，Sheehan Olver，Thomas Trogdon，Pennington

For more details, see for example [Yan Fyodorov](http://www.scholarpedia.org/article/Random_matrix_theory)

#### Distributions

+ [Wigner半圆定律](https://en.wikipedia.org/wiki/Wigner_semicircle_distribution)[bulk statistics]

the probability distribution supported on the interval [−R, R] the graph of whose probability density function f is a semicircle of radius R centered at (0, 0) and then suitably normalized (so that it is really a semi-ellipse)

$$f(x) = \frac{2}{\pi R^2} \sqrt{R^2 - x^2}$$

for -R ≤ x ≤ R, and f(x)=0 if |x| > R.

This distribution arises as the limiting distribution of eigenvalues of many random symmetric matrices as the size of the matrix approaches infinity.

It is a scaled beta distribution, more precisely, if Y is beta distributed with parameters α = β = 3/2, then X = 2RY – R has the above Wigner semicircle distribution.

In the limit of R approaching zero, the Wigner semicircle distribution becomes a Dirac delta function.

<u>In free probability theory, the role of Wigner's semicircle distribution is analogous to that of the normal distribution in classical probability theory.</u> Namely, in free probability theory, the role of cumulants is occupied by "free cumulants", whose relation to ordinary cumulants is simply that the role of the set of all partitions of a finite set in the theory of ordinary cumulants is replaced by the set of all noncrossing partitions of a finite set. Just as the cumulants of degree more than 2 of a probability distribution are all zero if and only if the distribution is normal, so also, the free cumulants of degree more than 2 of a probability distribution are all zero if and only if the distribution is Wigner's semicircle distribution.

In number-theoretic literature, the Wigner distribution is sometimes called the [Sato–Tate distribution](https://en.wikipedia.org/wiki/Sato–Tate_conjecture).

+ [Girko圆律](https://en.wikipedia.org/wiki/Circular_law): for non-Hermitian random matrices

+ Quartercircle law: singular values for normal Gaussian random matrices

+ [Marcenko-Pastur定律](https://en.wikipedia.org/wiki/Marčenko–Pastur_distribution)[bulk statistics]: describes the asymptotic behavior of singular values of large rectangular random matrices.

If X denotes a M×N random matrix whose entries are independent identically distributed random variables with mean 0 and variance σ<sup>2</sup> < ∞, let

$$Y_N = N^{-1} X X^T$$

and let λ<sub>1</sub>, λ<sub>2</sub>, …, λ<sub>M</sub> be the eigenvalues of Y<sub>N</sub> (viewed as random variables). Finally, consider the random measure

$$\mu_M(A) = \frac{1}{M} \#{\lambda_j \in A}, A \subset \mathbb{R}.$$

**Theorem.** Assume that M, N → ∞ so that the ratio M/N → λ ∈ (0,+ ∞). Then µ<sub>M</sub> → µ (in weak* topology in distribution), where

$$\mu(A) =\begin{cases} 
(1 - \frac{1}{\lambda}) \mathbf{1}_{0 \in A} + \nu(A), &\text{if} \lambda > 1\\
\nu(A), &\text{if} 0 \le \lambda \le 1,
\end{cases}$$

and

$$d\nu(x)=\frac{1}{2 \pi \sigma^2} \frac{\sqrt{(\lambda_+ - x)(x - \lambda_-)}}{\lambda x} \mathbf{1}_{[\lambda_-, \lambda_+]} dx$$

with

$$\lambda_{\pm} = \sigma^2 (1 \pm \sqrt{\lambda})^2.$$

The Marčenko–Pastur law also arises as the [free Poisson law](https://en.wikipedia.org/wiki/Free_Poisson_distribution) in free probability theory, having rate 1/λ and jump size σ<sup>2</sup>.

+ [Tracy-Widom定律](https://en.wikipedia.org/wiki/Tracy–Widom_distribution)[edge statistics]: the probability distribution of the normalized largest eigenvalue of a random Hermitian matrix.

$$F_2(s) = \lim_{n \rightarrow \infty} Prob\left( (\lambda_{max} - \sqrt{2n})(\sqrt{2})^{1/6} \le s \right),$$

The shift by √(2n) is used to keep the distributions centered at 0. The multiplication by (√2)n<sup>1/6</sup> is used because the standard deviation of the distributions scales as n<sup>-1/6</sup>.

The cumulative distribution function of the Tracy–Widom distribution can be given as the Fredholm determinant

$$F_2(s) = \det(I - A_s),$$

of the operator A<sub>s</sub> on square integrable functions on the half line (s, ∞) with kernel given in terms of Airy functions Ai by

$$\frac{\textrm{Ai}(x)\textrm{Ai}'(y) - \textrm{Ai}'(x)\textrm{Ai}(y)}{x - y}.$$

It can also be given as an integral

$$F_2(s) = \exp\left(-\int_s^\infty (x-s)q^2(x) dx \right)$$

in terms of a solution of a Painlevé equation of type II

$$q^{\prime\prime}(s) = sq(s)+2q(s)^3$$

where q, called the Hastings–McLeod solution, satisfies the boundary condition

$$\displaystyle q(s) \sim \textrm{Ai}(s), s\rightarrow\infty.$$

The distribution F<sub>2</sub> is associated to unitary ensembles in random matrix theory. There are analogous Tracy–Widom distributions F<sub>1</sub> and F<sub>4</sub> for orthogonal (β = 1) and symplectic ensembles (β = 4) that are also expressible in terms of the same Painlevé transcendent q

$$F_1(s)=\exp\left(-\frac{1}{2}\int_s^\infty q(x) dx\right)\left(F_2(s)\right)^{1/2}$$

and

$$F_4(s/\sqrt{2})=\cosh\left(\frac{1}{2}\int_s^\infty q(x) dx\right) \left(F_2(s)\right)^{1/2}.$$

In practical terms, Tracy–Widom is the crossover function between the two phases of weakly versus strongly coupled components in a system. It also appears in the distribution of the length of the longest increasing subsequence of random permutations (<u>Baik, Deift & Johansson 1999</u>), in current fluctuations of the <u>asymmetric simple exclusion process (ASEP)</u> with step initial condition (Johansson 2000, <u>Tracy & Widom 2009</u>), and in simplified mathematical models of the behavior of the longest common subsequence problem on random inputs.

The distribution F<sub>1</sub> is of particular interest in multivariate statistics (<u>Johnstone 2007, 2008, 2009</u>). For a discussion of the universality of F<sub>β</sub>, β = 1, 2, and 4, see <u>Deift (2007)</u>. For an application of F<sub>1</sub> to inferring population structure from genetic data see <u>Patterson, Price & Reich (2006)</u>. In 2017 it was proved that the distribution F is not infinitely divisible see <u>Domínguez-Molina, J. Armando 2017</u>.

For numerical approximations, see Edelman&Persson, Bornemann.

#### 其它性质

+ Edelman的奇异值分布
+ level spacings 分布
+ eigenvalue fluctuations
+ [free probability theory](https://en.wikipedia.org/wiki/Free_probability): Stieltjes transform, R transform[⊞], S transform[⊠]

#### Types

+ Ginibre ensemble

+ Gaussian ensemble

Gaussian measure with density: 

$$\frac{1}{Z_{\beta, n}}e^{-\frac{\beta n}{4}trH^2}$$ 

where β =1 for GOE, β =2 for GUE and β =4 for GSE.

joint probability density for the eigenvalues λ<sub>1</sub>, λ<sub>2</sub>, …, λ<sub>n</sub> of GOE/GUE/GSE: 

$$\frac{1}{Z_{\beta, n}} \prod_{k=1}^n e^{-\frac{\beta n}{4}\lambda_k^2} \prod_{i<j} \lvert \lambda_j - \lambda_i \rvert^{\beta}$$

In the case of GUE, the formula describes a <u>determinantal point process</u> with the sine kernel.

+ Wigner matrices/Toeplitz matrices/Circulant matrices/Hankel matrices

+ Laguerre ensemble

+ [Circular ensemble](https://en.wikipedia.org/wiki/Circular_ensemble): modification from Gaussian ensembles

+ Invariant ensemble

$$\frac{1}{Z_n}e^{-ntrV(H)}$$

where the function V is called the potential.

#### softwares
+ [Mathematica](https://www.wolfram.com/language/11/random-matrices/?product=mathematica)
+ [Python Packages](https://zenodo.org/record/579642)
+ Julia: RandomMatrices.jl

#### 应用

* 数学：Riemann zeta function，L function，正交多项式，HorngTzer Yau，Terry Tao，Alan Edelman，Peter Forrester
* 组合学：longest increasing subsequence
* 物理：原子核能级，固体行为，晶体学，totally asymmetric simple exclusion process，spin glass，量子物理，<u>量子混沌</u>，QCD，多体系统
* 数学物理：可积系统，Percy Deift，Tracy，Widom
* 信号处理：random matrix-based signal detection[Raj Rao Nadakuditi]，wireless communication[Tulino & Verdu]，Roman Couillet[Random matrix methods in wireless communications]，Robert C. Qiu's works on smart grid，compressed sensing[Donoho, Candes，Tao]
* 统计：random matrices in high-dimensional data analysis，Zhidong Bai，Jinho Baik，Silverstein，<u>Joel A Tropp</u>[An introduction to Matrix concentration inequalities]
* 金融统计：Wishart matrix，cross correlation in financial data
* 图论：Erdos-Renyi图
* 机器学习：<u>determinantal point process</u>，random matrices in data analysis[Dimitris Achlioptas]，matrix approximation，random matrices meet machine learning，Numerical Linear Algebra[Golub，Drineas，Mahoney，Gil Strang]
* 深度学习：Echo state machine，Extreme learning machine，</u>Roman Couillet</u>，<u>Jeffrey pennington</u>
* 复杂网络：<u>community detection in social network</u>，bus/subway arrival and departure analysis in a city，<u>Thomas Trogdon</u>


