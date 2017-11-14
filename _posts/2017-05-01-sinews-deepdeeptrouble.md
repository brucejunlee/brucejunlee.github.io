---
layout: post
title: "[SIAM NEWS] Deep, Deep Trouble"
author: "李军"
categories: journal
tags: [siam, deep learning]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

### Deep Learning’s Impact on Image Processing, Mathematics, and Humanity

By <u>Michael Elad</u>

May 01, 2017

[Michael Elad is a professor in the Computer Science Department at the Technion – Israel Institute of Technology. He is editor-in-chief of the SIAM Journal on Imaging Sciences.]

I am really confused. I keep changing my opinion on a daily basis, and I cannot seem to settle on one solid view of this puzzle. No, I am not talking about world politics or the current U.S. president, but rather something far more critical to humankind, and more specifically to our existence and work as engineers and researchers. I am talking about…deep learning.

While you might find the above statement rather bombastic and overstated, deep learning indeed raises several critical questions we must address. In the following paragraphs, I hope to expose one key conflict related to the emergence of this field, which is relevant to researchers in the image processing community.

First, a few words about deep learning to put our discussion into perspective. Neural networks have been around for decades, proposing a universal learning mechanism that could, in principle, fit to any learnable data source. In its feed-forward architecture, layers of perceptrons—also referred to as neurons—first perform weighted averaging of their inputs, followed by nonlinearities such as a sigmoid or rectified-linear curves. One can train this surprisingly simple system to fit a given input set to its desired output, serving various supervised regression and classification problems.

All of this may sound great, but unfortunately this concept did not take off in the 1980s and 90s — it simply did not provide a sufficiently competitive performance. In addition, the emergence of support vector machines for learning tasks, accompanied by solid theoretical foundations and a convex optimization formulation, seemed to be the last nail in the coffin. Eventually, neural networks entered a long hibernation period. Only a few persistent researchers—Yann LeCun (New York Univerity and Facebook), Geoffrey Hinton (University of Toronto), Yoshua Bengio (University of Montreal), and Jürgen Schmidhuber (Dalle Molle Institute for Artificial Intelligence Research)—stayed in this arena, insisting on trying to convince this seemingly doomed method to behave better. Several important architectures, such as convolutional and long short-term memory networks, resulted from their efforts; yet they were still confined to a niche. Then neural networks suddenly came back, and with a vengeance.

A series of papers during the early 2000s suggested the successful application of this architecture, leading to state-of-the-art results in practically any assigned task. Key aspects in these contributions included the following: the use of many network layers, which explains the term “deep learning;” a huge amount of data on which to train; massive computations typically run on computer clusters or graphic processing units; and wise optimization algorithms that employ effective initializations and gradual stochastic gradient learning. Unfortunately, all of these great empirical achievements were obtained with hardly any theoretical understanding of the underlying paradigm. Moreover, the optimization employed in the learning process is highly non-convex and intractable from a theoretical viewpoint.

This application effort began with written digit recognition (see Figure 1), moving slowly and carefully to more challenging visual and speech recognition and natural language processing tasks, and from there on to practically anything that could be cast as a supervised learning task. Companies such as Google, Facebook, and Microsoft quickly realized the potential in this field and invested massive manpower and budget in order to master these tools and exploit them in their products. On the academic front, conferences in signal processing, image processing, and computer vision have become deep learning playgrounds, contributing to a growing dominance of this bread of work.

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-deepdeeptrouble-1.jpg)

**Figure 1.** Neural networks have shown great potential, first in character recognition and subsequently in many other tasks. Image credit: Michael Elad.

This history brings us to present day. For the sake of brevity, consider the classic image processing task of denoising — removing noise from an image (see Figure 2). Thousands of papers addressing this fundamental task were written over the years. Researchers developed beautiful and deep mathematical ideas with tools from partial differential equations, such as anisotropic diffusion and total variation, energy minimization viewpoint, adoption of a geometric interpretation of images as manifolds, use of the Beltrami flow, and more. Harmonic analysis and approximation theory have also served the denoising task, leading to major breakthroughs with wavelet theory and sparse representations. Other brilliant ideas included low-rank approximation, non-local means, Bayesian estimation, and robust statistics. We have hence gained vast knowledge in image processing over the past three decades, impacting many other image processing tasks and effectively upgrading this field to be mathematically well-founded.

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-deepdeeptrouble-2.jpg)

**Figure 2.** A denoising example. Left. An original image (public domain). Middle. Image contaminated by additive Gaussian noise of STD=100. Right. The denoising outcome obtained by one of the leading algorithms — the BM3D [1]. Image credit: Michael Elad.

In 2012, Harold Burger, Christian Schuler, and Stefan Harmeling decided to throw deep learning into this problem. The idea was conceptually quite simple: take a huge set of clean images, add synthetic noise, and then feed them to the learning process that aims to turn a noisy image into its clean version. While the process was tedious, frustrating, and lengthy—tweaking the method’s parameters in a search for good performance likely took a long time—the end result was a network that performed better than any known image denoising algorithm at that time.

The above is not an isolated story. Today, deep learning treats many other image processing needs, with unsurpassed results. This is true for single image super-resolution, demosaicing, deblurring, segmentation, image annotation, and face recognition, among others.

Should we be happy about this trend? Well, if we are in the business of solving practical problems such as noise removal, the answer must be positive. Right? Therefore, a company seeking such a solution should be satisfied. But what about us scientists? What is the true objective behind the vast effort that we invested in the image denoising problem? Yes, we do aim for effective noise-removal algorithms, but this constitutes a small fraction of our motivation, as we have a much wider and deeper agenda. Researchers in our field aim to understand the data on which we operate. This is done by modeling information in order to decipher its true dimensionality and manifested phenomena. Such models serve denoising and other problems in image processing, but far more than that, they allow identifying new ways to extract knowledge from the data and enable new horizons.

Now back to the main question: should we be pleased about emerging solutions based on deep learning? Is our frustration justified? What is the role of deep learning in imaging science? These questions present themselves when researchers in the community meet at conferences, and the answers are diverse and confusing. The facts speak loudly for themselves; in most cases, deep learning-based solutions lack mathematical elegance and offer very little interpretability of the found solution or understanding of the underlying phenomena. On the positive side, however, the performance obtained is terrific. This is clearly not the school of research we have been taught, and not the kind of science we want to practice. Should we insist on our more rigorous ways, even at the cost of falling behind in terms of output quality? Or should we fight back and seek ways to fuse ideas from deep learning into our more solid foundations?

To further complicate this story, certain deep learning-based contributions bear some elegance that cannot be dismissed. Such is the case with the style-transfer problem, which yielded amazingly beautiful results, and with inversion ideas of learned networks used to synthesize images out of thin air, as Google’s Deep Dream project does. A few years ago we did not have the slightest idea how to formulate such complicated tasks; now they are solved formidably as a byproduct of a deep neural network trained for the completely extraneous task of visual classification.

From my personal viewpoint, image processing researchers have mixed feelings of disgust and envy towards this recent trend of deep learning that keeps pushing itself into our court. Some of us have chosen to remain bystanders for now, while others play along and divert their research agendas accordingly. I belong to the latter group, with some restrictions. In my opinion, it is impossible to imagine that this wave will pass without a marked influence on our field. Thus, I allow deep learning to influence my research team’s thoughts and actions, but we continue to insist on seeking mathematical elegance and a clear understanding of the ideas we develop. Time will tell if we are aiming for the impossible.

Briefly circling back to my opening statement on deep learning’s massive impact on humankind, human lives will likely be very different several decades into the future. Humanoid robots and intelligence systems might surround us and influence many of our activities, employment and jobs may be things of the past, and relationships between people will probably change drastically. To put it bluntly, your grandchild is likely to have a robot spouse. And here is the punch line: much of the technology behind this bizarre future is likely to emerge from deep learning and its descendant fields.

While this technology progresses rapidly, we haven’t stopped to think if this is the future we want for ourselves. The curiosity and tremendous talent of engineers and researchers is driving us towards this future, as do companies that see profit as their main goal. How is it that we rarely engage in discussion about regulating or controlling this progress and guiding it towards a desired future? This is a matter for a different article.

What are your thoughts on the impact of deep learning on image processing — and humanity? Share your feedback by sending us a letter to the editor or blog post at sinews@siam.org, or post a comment below.

**Acknowledgments:** The author would like to thank Alex Bronstein and Ron Kimmel for valuable comments, which helped tune the message of this article.

References

[1] Dabov, K., Foi, A., Katkovnik, V., & Egiazarian, K. (2007). Color image denoising via sparse 3D collaborative filtering with grouping constraint in luminance-chrominance space. Proc. IEEE Int. Conf. Image Process., 1, I-313-I-316.