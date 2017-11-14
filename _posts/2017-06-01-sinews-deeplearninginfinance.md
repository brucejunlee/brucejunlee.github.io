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

Deep learning, a subfield of machine learning that uses “deep neural networks,” has achieved state-of-the-art results in fields such as image and text recognition. A deep neural network is a neural network with many hidden layers, which allow it to model complex nonlinear functions more effectively than single-layer neural networks. Deep learning focuses on the development of specific model architectures and training methods to enhance the performance of multilayer neural networks. Deep neural networks, which have a large number of parameters, are typically trained on large amounts of data to avoid overfitting. Training is very computationally expensive due to the complexity of the deep neural network model and the large amount of data. Models are often trained for multiple days on clusters of graphics processing units.

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-deeplearninginfinance-1.jpg)

Figure 1. Bid and ask sizes for the first 15 bid and ask prices for Microsoft. Level 0 is the best ask price. Image courtesy of [11].

Deep learning research has made continual advances over the last decade. Researchers have designed new optimization methods (Adam, RMSprop, and others) to better train the highly nonconvex neural networks. Regularization methods such as dropout help reduce overfitting [14], and ever deeper neural networks are trained. For example, [7] trains a neural network with 1,000 layers. Deep reinforcement learning has successfully combined deep neural networks with reinforcement learning algorithms to learn complex tasks. For example, researchers have trained deep neural networks to play a range of Atari video games using only the raw pixels from the screen (similar to how a human watches the game) [10]. An overview of deep learning models and methods can be found in [3].

Despite the immense success of machine learning in other fields, there is very little published research on its application to finance, and almost none on deep learning.

**Applications of Deep Learning in Finance**

Today, stocks are frequently traded via electronic exchanges (e.g., NASDAQ and NYSE Arca). Traders continuously submit, cancel, and execute buy and sell orders in the exchange’s limit order book. Market events are often reported at the nanosecond granularity, and therefore the limit order book data generated over time is very large (terabytes to petabytes). Deep learning can model key quantities, such as the probability distribution of future price movements given the current state of supply and demand in the market. An example is presented in [11].

The limit order book represents the known supply and demand for a stock at different price levels at any particular point in time. It consists of all existing orders at all prices. The “bids” are the buy orders and the “asks” are the sell orders. The best ask price is the lowest sell order, while the best bid price is the highest buy order. The mid-price (the average of the best bid and best ask prices) is often called the “price” of the stock. However, it is an artificial quantity, since one cannot buy or sell a stock at the mid-price. The best ask price and best bid price are the actual prices at which one can respectively buy or sell the stock.

Figure 1 shows an example of the limit order book for Microsoft. The size at level k is the number of shares available in the limit order book to be bought/sold at k discrete price levels from the best ask price. Over time, the limit order book (and the best ask and best bid prices) will evolve due to new limit orders, cancellations, and market orders.

A recent paper [11] trains deep learning models to predict the movement of the best ask and best bid prices. It uses a dataset of 489 stocks and tests on a three month out-of-sample period. The histogram in Figure 2 shows an example of a neural network’s performance gain compared to a logistic regression model across the 489 stocks. Figure 2 presents the results for predicting the next price move of the best ask price. See [11] for details.

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-deeplearninginfinance-2.jpg)

Figure 2. Increase in out-of-sample accuracy of neural network over logistic regression. Accuracies are measured in percentages. Results are depicted for the marginal distribution of the best ask price at the time of the next price move. Image courtesy of [11].

Another promising application of deep learning is for modeling loan risk. [6] develops and tests a deep learning model for mortgage risk on data from tens of millions of loans. Besides loan-level predictions, the model can be used to select mortgage investment portfolios. Other examples of deep learning in finance include [2] and [8].

**Mathematical Analysis in Machine Learning and Deep Learning**

There are also opportunities for the mathematical analysis of machine learning and deep learning algorithms (not necessarily specific to finance). Although successful in practice, deep learning methods are often ad hoc and therefore present an exciting opportunity for more rigorous analysis. A recent example is [9], where Stéphane Mallat develops a mathematical approach to understand the success of deep convolution neural networks. A convolution neural network is a type of neural network architecture that has proven incredibly successful at image classification. Examples closer to the field of mathematical finance include [1], [4-6], and [13].

[13] studies stochastic gradient descent in continuous time (SGDCT). SGDCT provides a computationally efficient method for statistical learning of continuous-time models, which are widely used in finance, engineering, and science. The algorithm follows a (noisy) descent direction along a continuous stream of data. [13] proves convergence of the continuous-time stochastic gradient descent algorithm. The analysis relies upon describing the parameter behavior for large times using a type of Poisson partial differential equation. Besides model estimation, SGDCT can also be used for the optimization of high-dimensional continuous-time models, such as American options. High-dimensional American options have been a longstanding computational challenge in finance. [13] successfully combines SGDCT with a deep neural network to solve American options in up to 100 dimensions.

**Future Opportunities**

There are a broad range of opportunities for (1) the development of new deep learning models and methods for financial applications and (2) mathematical analysis of these machine learning approaches. It is the hope of this article to highlight some of these opportunities and encourage future research in these areas.

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