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

Well, maybe not “hard,” but certainly time consuming and computationally very expensive. Perhaps the quantity to be minimized can be calculated only by some creaky piece of legacy code. Or its evaluation may demand code packaged in a black box, possibly proprietary. Or it might require using a complex, long-running simulation—or even conducting an entire experiment—for every scenario considered. All of these very real possibilities have arisen as the world’s appetite for optimal has grown.

In an invited lecture at the 2016 SIAM Annual Meeting, Stefan Wild (Argonne National Laboratory) addressed this class of optimization problems. He emphasized that the challenge arises because the computational cost of evaluating the objective function overwhelms every other aspect of finding an optimum, not because the objective function lacks derivatives.

For example, Wild and Christine Shoemaker (Cornell University) have described the problem of finding optimal pumping strategies to reduce hazardous waste contamination of groundwater: a series of wells, operating over a range of pumping rates, can inject pure water or remove and treat contaminated water. What is the least-cost pumping strategy for 15 wells operating over 30 years, say, to bring the concentration of hazardous agents in the aquifer within the standards of the Environmental Protection Agency? Evaluating a single scenario requires a time-consuming (45+ minutes) groundwater flow simulation.

That simulation code is too complex to permit algorithmic differentiation, which involves processing the code to produce new code able to evaluate specific derivatives of the objective function. Numerical differentiation and genetic algorithms each encounter the same bottleneck of computational cost: the time needed for a single function evaluation—a complete run of the underlying groundwater simulation—far exceeds every other aspect of the computation.

Philosophically, Wild’s approach is to “make the most of little,” to exploit the values of the objective function at selected points in order to determine a productive direction for the next minimization step. His setting is a model-based trust region, a compact region over which the objective function is well modeled by a quadratic approximation. The trust region grows or shrinks as it moves with the minimization steps.

To “make the most” of the expensive objective function evaluations, Wild chooses the interpolation points so that the approximation error in the quadratic model of the objective obeys Taylor-like bounds. That is, the error in the function approximation is bounded by the square of a measure of the spacing of the interpolation points and the error in approximating the derivative by its first power. Such models are called fully linear. Parallel considerations guide the choice of the interpolation basis functions.

Since his presentation also provided quick comparisons to a variety of related approaches, Wild had little time for details that illustrate the efficiencies offered by fully linear models. For example, fitting a unique quadratic in n variables (n=15 pumping rates +... in the contaminated groundwater example) requires (n+1)(n+2)/2 evaluations of the objective. The value of the fully linear model is its reliance on significantly fewer interpolation points while its gradient still points in the direction of a cheaper operating point.

The overhead of fulfilling the geometric conditions on the interpolation points to achieve fully linear models and the effort of building the model of the objective are small change compared to the exorbitant cost of evaluating the objective function.

In pursuit of “lower minimum values with fewer black-box function evaluations,” Wild advocates “exploiting as much structure as is known” before employing the algorithmic structure of the fully linear model trust region approach. Least squares problems, for example, minimize a sum of squared residuals, some of which may be expensive to compute. The gradient of the objective involves products of individual residuals and their respective gradients. Wild approximates the gradient of each residual term with the gradient of its corresponding quadratic model. For least absolute value problems, Wild notes that because we “know the location of the singularities [we can] use a model-based approximation away from the nuisance points.”

And the value of these efficient strategies? “We are closer and closer to being able to optimize virtually everything,” Wild says.

**Further Reading**

Wild, S.M., & Shoemaker, C. (2013).  Global Convergence of Radial Basis Function Trust-Region Algorithms for Derivative-Free Optimization. SIAM Review, 55(2), 349-371.