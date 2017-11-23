---
layout: post
title: "[SIAM NEWS] Deep Learning Models in Finance"
author: "李军"
categories: journal
tags: [siam, deep learning]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

By <u>Justin Sirignano</u>

June 01, 2017

[Justin Sirignano is an assistant professor at the University of Illinois at Urbana-Champaign. His research interests include machine learning, optimization, applied probability, and financial applications.]

The finance literature has historically focused on stochastic models and their mathematical analysis. However, unlike in physics or other sciences, there are no fundamental laws in finance (such as Newton’s laws) from which to derive models; therefore, some assumptions must be made. A purely data-driven approach, such as machine learning, is potentially superior for some applications. Opportunities exist for both the development of new machine learning models for financial applications and the mathematical analysis of these statistical learning algorithms.

从历史来看，金融文献主要关注随机模型以及它们的数学分析。但是，不像物理或其它科学，在金融中并没有可以推导出模型的基本定律（如牛顿定律）；因此，我们需要作一些假设。一个如机器学习等纯数据驱动的方法在一些应用中更占优。在金融应用中新的机器学习模型的开发以及这些统计学习算法的数学分析方面都有很多机遇。

Deep learning, a subfield of machine learning that uses “deep neural networks,” has achieved state-of-the-art results in fields such as image and text recognition. A deep neural network is a neural network with many hidden layers, which allow it to model complex nonlinear functions more effectively than single-layer neural networks. Deep learning focuses on the development of specific model architectures and training methods to enhance the performance of multilayer neural networks. Deep neural networks, which have a large number of parameters, are typically trained on large amounts of data to avoid overfitting. Training is very computationally expensive due to the complexity of the deep neural network model and the large amount of data. Models are often trained for multiple days on clusters of graphics processing units.

作为使用“深度神经网络”的机器学习的一个子领域，深度学习在如图像和文本识别等领域中实现了当前最好的结果。一个深度神经网络是拥有很多隐含层的神经网络，这样的结构可以比单层神经网络更高效地建模复杂的非线性函数。深度学习关注特定的模型架构和增强多层神经网络性能的训练方法的开发。包含大量参数的深度神经网络通常为了避免过拟合在大量数据上进行训练。由于深度神经网络模型以及大量数据的复杂性，模型的训练从计算上来看代价是非常高的。模型经常需要在GPU集群上训练很多天。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-deeplearninginfinance-1.jpg)

Figure 1. Bid and ask sizes for the first 15 bid and ask prices for Microsoft. Level 0 is the best ask price. Image courtesy of [11].

Deep learning research has made continual advances over the last decade. Researchers have designed new optimization methods (Adam, RMSprop, and others) to better train the highly nonconvex neural networks. Regularization methods such as dropout help reduce overfitting [14], and ever deeper neural networks are trained. For example, [7] trains a neural network with 1,000 layers. Deep reinforcement learning has successfully combined deep neural networks with reinforcement learning algorithms to learn complex tasks. For example, researchers have trained deep neural networks to play a range of Atari video games using only the raw pixels from the screen (similar to how a human watches the game) [10]. An overview of deep learning models and methods can be found in [3].

深度学习研究在过去几十年已经取得了很大进展。研究者已经设计了很多新的优化方法（如Adam，RMSprop等）来更好地训练高度非凸神经网络。如dropout等正则化方法有助于减少过拟合[14]，从而训练更深的神经网络。例如，[7]训练了一个具有1000层的神经网络。深度强化学习已经成功组合了深度神经网络和强化学习算法来学习复杂任务。比如，研究者训练深度神经网络只使用来自屏幕的原始像素来玩Atari视频游戏（这与人类观看游戏很相似）[10]。深度学习模型和方法的概述可以在[3]中找到。

Despite the immense success of machine learning in other fields, there is very little published research on its application to finance, and almost none on deep learning.

尽管机器学习在其它领域中取得了巨大成功，但它在金融中已发行的研究还很少，关于深度学习的更是几乎没有。

**Applications of Deep Learning in Finance**

**深度学习在金融中的应用**

Today, stocks are frequently traded via electronic exchanges (e.g., NASDAQ and NYSE Arca). Traders continuously submit, cancel, and execute buy and sell orders in the exchange’s limit order book. Market events are often reported at the nanosecond granularity, and therefore the limit order book data generated over time is very large (terabytes to petabytes). Deep learning can model key quantities, such as the probability distribution of future price movements given the current state of supply and demand in the market. An example is presented in [11].

今天，股票通过电子交易所（如NASDAQ，NYSE Arca）频繁交易。交易员不断在交易所的限价簿上提交，取消和执行买卖订单。市场事件经常以纳秒级粒度报告，因此随着时间产生的限价簿数据非常大（TB到PB）。深度学习可以建模关键量，如给定目前市场供需状态下未来价格活动的概率分布。[11]给出了一个例子。

The limit order book represents the known supply and demand for a stock at different price levels at any particular point in time. It consists of all existing orders at all prices. The “bids” are the buy orders and the “asks” are the sell orders. The best ask price is the lowest sell order, while the best bid price is the highest buy order. The mid-price (the average of the best bid and best ask prices) is often called the “price” of the stock. However, it is an artificial quantity, since one cannot buy or sell a stock at the mid-price. The best ask price and best bid price are the actual prices at which one can respectively buy or sell the stock.

限价簿表示的是在任何特定时间点上不同价格水平的股票的供需关系。它包括已经存在的所有价格的订单。投标是买入订单，要价是卖出订单。最好的要价也就是最低的卖出订单，然而最好的投标价格是最高的买入订单。中间价（最好投标和最好要价的平均）经常被称为股价。但是这只是一个人造量，因为人们并不能在中间价处买卖股票。最好的卖出价格和最好的买入价格是人们各自可以买卖的实际价格。

Figure 1 shows an example of the limit order book for Microsoft. The size at level k is the number of shares available in the limit order book to be bought/sold at k discrete price levels from the best ask price. Over time, the limit order book (and the best ask and best bid prices) will evolve due to new limit orders, cancellations, and market orders.

图 1 给出了一个微软限价簿的例子。在k水平上的量就是在限价簿中离最好的卖出价格k个离散价格水平上可供买卖的股份数。由于新的限价订单、取消订单和市场订单，限价簿（以及最好卖出价格和最好买入价格）将随着时间发展。

A recent paper [11] trains deep learning models to predict the movement of the best ask and best bid prices. It uses a dataset of 489 stocks and tests on a three month out-of-sample period. The histogram in Figure 2 shows an example of a neural network’s performance gain compared to a logistic regression model across the 489 stocks. Figure 2 presents the results for predicting the next price move of the best ask price. See [11] for details.

最近的一篇论文 [11] 训练深度学习模型来预测最好卖出价格和最好买入价格活动。它使用一个包含489支股票的数据集，并在三个月样本期内进行了测试。图 2 中的柱状图展示了一个相对于横跨这489支股票的逻辑回归模型的神经网络模型的性能增益的例子。图 2 给出了预测最好卖出价格的下一个价格运动的结果。具体细节看 [11] 。

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-deeplearninginfinance-2.jpg)

Figure 2. Increase in out-of-sample accuracy of neural network over logistic regression. Accuracies are measured in percentages. Results are depicted for the marginal distribution of the best ask price at the time of the next price move. Image courtesy of [11].

Another promising application of deep learning is for modeling loan risk. [6] develops and tests a deep learning model for mortgage risk on data from tens of millions of loans. Besides loan-level predictions, the model can be used to select mortgage investment portfolios. Other examples of deep learning in finance include [2] and [8].

另一个被看好的深度学习应用是建模借款风险。[6] 在数以千万计的借款数据上开发和测试了一个抵押贷款风险的深度学习模型。除了借款预测外，该模型还能用于选择抵押贷款投资组合。其它运用于金融的深度学习事例包括 [2] 和 [8] 。

**Mathematical Analysis in Machine Learning and Deep Learning**

**机器学习和深度学习中的数学分析**

There are also opportunities for the mathematical analysis of machine learning and deep learning algorithms (not necessarily specific to finance). Although successful in practice, deep learning methods are often ad hoc and therefore present an exciting opportunity for more rigorous analysis. A recent example is [9], where Stéphane Mallat develops a mathematical approach to understand the success of deep convolution neural networks. A convolution neural network is a type of neural network architecture that has proven incredibly successful at image classification. Examples closer to the field of mathematical finance include [1], [4-6], and [13].

对于机器学习和深度学习算法（不特定于金融）的数学分析也存在很多机遇。深度学习方法尽管实践中很成功，但经常是特别的，因此给更加严格的分析提供了很好的机遇。最近的一个例子是 [9] ，在这篇文章中Stéphane Mallat开发了一种数学方法用于理解深度卷积神经网络的成功。一个卷积神经网络是一类已经被证明在图像分类问题上非常成功的神经网络架构。与数学金融领域更接近的例子包括[1]，[4-6] 和 [13] 。

[13] studies stochastic gradient descent in continuous time (SGDCT). SGDCT provides a computationally efficient method for statistical learning of continuous-time models, which are widely used in finance, engineering, and science. The algorithm follows a (noisy) descent direction along a continuous stream of data. [13] proves convergence of the continuous-time stochastic gradient descent algorithm. The analysis relies upon describing the parameter behavior for large times using a type of Poisson partial differential equation. Besides model estimation, SGDCT can also be used for the optimization of high-dimensional continuous-time models, such as American options. High-dimensional American options have been a longstanding computational challenge in finance. [13] successfully combines SGDCT with a deep neural network to solve American options in up to 100 dimensions.

[13] 研究了连续时间上的随机梯度下降法（stochastic gradient descent in continuous time，SGDCT）。SGDCT为连续时间模型（这被广泛用于金融、工程和科学）上的统计学习提供了一个计算上很高效的方法。算法沿着（带噪声的）下降方向通过连续数据流。[13] 证明了连续时间随机梯度下降算法的收敛性。该分析依赖于使用一类Poisson PDEs来描述长时间的参数行为。除了模型估计外，SGDCT还可以用于高维连续时间模型的优化，如美式期权。高维美式期权是金融中一个存在已久的计算挑战。[13] 成功地将SGDCT和深度神经网络组合起来解决了高达100维德美式期权。

**Future Opportunities**

**未来机遇**

There are a broad range of opportunities for (1) the development of new deep learning models and methods for financial applications and (2) mathematical analysis of these machine learning approaches. It is the hope of this article to highlight some of these opportunities and encourage future research in these areas.

对于（1）金融应用中新的深度学习模型和方法的开发以及（2）这些机器学习方法的数学分析有很多机遇。这篇文章希望突出这些机遇以及鼓励这些领域的未来研究。

References

[1] Ban, G-Y., Karoui, N.E., & Lim, A.E.B. (2016). Machine Learning and Portfolio Optimization. Management Science.

[2] Dixon, M., Klabjan, D., & Bang, J. (2016). Classification-based Financial Markets Prediction Using Deep Neural Networks. Algorithmic Finance.

[3] Goodfellow, I., Bengio, Y., & Courville, A. (2016). Deep Learning. In T. Dietterich (Ed.), Adaptive Computation and Machine Learning. Cambridge, MA: MIT Press. 

[4] Hazan, E., & Kale, S. (2009). On Stochastic and Worst-case Models for Investing. Advances in Neural Information Processing Systems, 22.

[5] Hazan, E., & Kale, S. (2012). An Online Portfolio Selection Algorithm with Regret Logarithmic in Price Variation. Mathematical Finance, 25(2), 288-310.

[6] He, N., Harchaoui, Z., Wang, Y., & Song, L. (2016). Fast and Simple Optimization for Poisson Likelihood Models. arXiv:1608.01264.

[7] He, K., Zhang, X., Ren, S., & Sun, J. (2016). Deep Residual Learning for Image Recognition. In 2016 IEEE Conference on Computer Vision and Pattern Recognition (CVPR). Las Vegas, NV: Institute of Electrical and Electronics Engineers.

[8] Heaton, J., Polson, N., & Witte, J. (2016). Deep Portfolio Theory. arXiv:1605.07230.

[9] Mallat, S. (2016). Understanding deep convolutional networks. Philosophical Transactions of the Royal Society A, 374(2065). 

[10] Mnih, V., Kavukcuoglu, K., Silver, D., Rusu, A., Veness, J., Bellemare, M.,…Hassabis, D. (2015). Human-level control through deep reinforcement learning. Nature, 518, 529-533. 

[11] Sirignano, J. (2016). Deep Learning for Limit Order Books. arXiv:1601.01987.

[12] Sirignano, J., Sadhwani, A., & Giesecke, K. (2016). Deep Learning for Mortgage Risk. arXiv:1607.02470

[13] Sirignano, J., & Spiliopoulos, K. (2016). Stochastic Gradient Descent in Continuous Time. arXiv:1611.05545.

[14] Srivastava, N., Hinton, G., Krizhevsky, A., Sutskever, I., & Salakhutdinov, R. (2014). Dropout: A Simple Way to Prevent Neural Networks from Overfitting. Journal of Machine Learning Research, 15, 1929-1958.