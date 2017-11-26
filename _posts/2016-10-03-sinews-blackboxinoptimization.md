---
layout: post
title: "[SIAM NEWS] Looking Beyond the Black Box in Optimization"
author: "李军"
categories: journal
tags: [siam, optimization]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

By Paul Davis

October 03, 2016

[Paul Davis is professor emeritus of mathematical sciences at Worcester Polytechnic Institute.]

Optimization problems can be hard for many reasons. But how often is the challenge of such a problem the evaluation of the objective function? How hard can it be to crank out a single number?

优化问题的难度有很多原因。但是对目标函数的评估这样一个问题的挑战是否经常呢？计算一个数字有多难呢？

Well, maybe not “hard,” but certainly time consuming and computationally very expensive. Perhaps the quantity to be minimized can be calculated only by some creaky piece of legacy code. Or its evaluation may demand code packaged in a black box, possibly proprietary. Or it might require using a complex, long-running simulation—or even conducting an entire experiment—for every scenario considered. All of these very real possibilities have arisen as the world’s appetite for optimal has grown.

嗯，也许不“难”，但肯定很费时，计算上也非常昂贵。也许这些被最小化的量只能通过一些陈旧的遗留代码块来计算。或者它的评估可能要求代码封装在可能有专卖权的黑盒中。或者它可能需要使用复杂的、长时间运行的模拟，或许甚至对每个场景都进行一个完整的实验。随着全世界对最优的需求增长，所有这些真实的可能性也随之出现了。

In an invited lecture at the 2016 SIAM Annual Meeting, Stefan Wild (Argonne National Laboratory) addressed this class of optimization problems. He emphasized that the challenge arises because the computational cost of evaluating the objective function overwhelms every other aspect of finding an optimum, not because the objective function lacks derivatives.

在2016年SIAM年会的一个受邀演讲中，来自Argonne National Laboratory的Stefan Wild处理了这类优化问题。他强调挑战的出现，是由于评估目标函数的计算成本压倒了找到一个最优点的所有其他方面，而不是因为目标函数缺少导数。

For example, Wild and Christine Shoemaker (Cornell University) have described the problem of finding optimal pumping strategies to reduce hazardous waste contamination of groundwater: a series of wells, operating over a range of pumping rates, can inject pure water or remove and treat contaminated water. What is the least-cost pumping strategy for 15 wells operating over 30 years, say, to bring the concentration of hazardous agents in the aquifer within the standards of the Environmental Protection Agency? Evaluating a single scenario requires a time-consuming (45+ minutes) groundwater flow simulation.

例如，Wild和来自康奈尔大学的Christine Shoemaker已经描述了寻找最优抽水策略以减少地下水的有害废物污染的问题：在一定范围的抽水速率下运行的一系列水槽，可以注入纯净水或者抽除并处理受污染的水。比如说，15个水槽连续作业超过30年，将污染水集中在符合美国环境保护署标准的含水层，最低抽水成本是多少呢？评估一个简单的场景就需要一个非常耗时的（45分钟以上）地下水流仿真。

That simulation code is too complex to permit algorithmic differentiation, which involves processing the code to produce new code able to evaluate specific derivatives of the objective function. Numerical differentiation and genetic algorithms each encounter the same bottleneck of computational cost: the time needed for a single function evaluation—a complete run of the underlying groundwater simulation—far exceeds every other aspect of the computation.

该仿真代码太复杂以至于不能进行算法微分，这涉及到处理代码以产生新的能够评估目标函数的特定导数的代码。数值微分和遗传算法都会遇到计算成本上同样的瓶颈：单个函数评估所需的时间（也就是一次完整的地下水模拟）远远超出了所有其他方面的计算。

Philosophically, Wild’s approach is to “make the most of little,” to exploit the values of the objective function at selected points in order to determine a productive direction for the next minimization step. His setting is a model-based trust region, a compact region over which the objective function is well modeled by a quadratic approximation. The trust region grows or shrinks as it moves with the minimization steps.

从哲学上讲，Wild的方法是“充分利用小”使用选定点处目标函数值，以确定下一个最小化步骤中的一个有效方向。他的设置是一个基于模型的置信区域，这是一个紧致区域，在这个区域上目标函数可以通过二次近似很好地建模。置信区域将随着最小化步骤移动而增长或缩小。

To “make the most” of the expensive objective function evaluations, Wild chooses the interpolation points so that the approximation error in the quadratic model of the objective obeys Taylor-like bounds. That is, the error in the function approximation is bounded by the square of a measure of the spacing of the interpolation points and the error in approximating the derivative by its first power. Such models are called fully linear. Parallel considerations guide the choice of the interpolation basis functions.

为了最大限度利用昂贵的目标函数评估，Wild选择插值点，使目标的二次模型中的近似误差服从类Taylor界限。也就是说，函数近似中的误差是由插值点间距测量的平方以及使用它的一阶幂近似导数而产生的误差所限的。这种模型被称为完全线性的。并行考虑可以指导插值基函数的选择。

Since his presentation also provided quick comparisons to a variety of related approaches, Wild had little time for details that illustrate the efficiencies offered by fully linear models. For example, fitting a unique quadratic in n variables (n=15 pumping rates +... in the contaminated groundwater example) requires (n+1)(n+2)/2 evaluations of the objective. The value of the fully linear model is its reliance on significantly fewer interpolation points while its gradient still points in the direction of a cheaper operating point.

由于他的陈述中还给出了各种相关方法的快速比较，所以Wild几乎没有时间来详细说明完全线性模型所能提供的高效性。例如，拟合唯一的n变量二次型（n＝15个不同的抽运率+在受污染地下水例子中的…）需要对目标进行(n+1)(n+2)/2次评估。完全线性模型的值依赖于较少的插值点，然而其梯度仍然指向较便宜的操作点方向。

The overhead of fulfilling the geometric conditions on the interpolation points to achieve fully linear models and the effort of building the model of the objective are small change compared to the exorbitant cost of evaluating the objective function.

与评价目标函数的过高成本相比，在插值点上实现完全线性模型而完成几何条件的开销和建立目标模型的努力都是小变化。

In pursuit of “lower minimum values with fewer black-box function evaluations,” Wild advocates “exploiting as much structure as is known” before employing the algorithmic structure of the fully linear model trust region approach. Least squares problems, for example, minimize a sum of squared residuals, some of which may be expensive to compute. The gradient of the objective involves products of individual residuals and their respective gradients. Wild approximates the gradient of each residual term with the gradient of its corresponding quadratic model. For least absolute value problems, Wild notes that because we “know the location of the singularities [we can] use a model-based approximation away from the nuisance points.”

在“使用较少的黑盒函数评估的情况下尽可能追求更低的最小值”时，Wild主张“在使用完全线性模型置信区域方法前应该充分利用尽可能多已知的结构”。例如，最小二乘问题就是最小化平方残差和，其中一些可能是比较昂贵的计算。目标函数的梯度包括每个残差和它们各自梯度的乘积。Wild使用相应二次型模型中的梯度来近似每个残差项的梯度。对于最小绝对值问题，Wild指出，因为我们“知道奇点位置，所以我们可以使用远离麻烦点的基于模型的近似”。

And the value of these efficient strategies? “We are closer and closer to being able to optimize virtually everything,” Wild says.

这些高效策略的价值何在呢？Wild说“我们越来越能够优化几乎所有的东西”。

**Further Reading**

Wild, S.M., & Shoemaker, C. (2013).  Global Convergence of Radial Basis Function Trust-Region Algorithms for Derivative-Free Optimization. SIAM Review, 55(2), 349-371.