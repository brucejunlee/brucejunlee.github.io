---
layout: post
title: "[SIAM NEWS] Probing the Deep Mathematics of Nonlinear Inverse Problems"
author: "李军"
categories: journal
tags: [siam, math]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

By <u>Samuli Siltanen</u>

June 01, 2012

[Samuli Siltanen is a professor at the University of Helsinki and the SIAM News liaison for the SIAM Activity Group on Imaging Science.]

As the SIAM News liaison for the SIAM Activity Group on Imaging Science, Samuli Siltanen suggested that readers might be interested in the work of the most recent recipient of the Calderón Prize, Guillaume Bal. The prize, given biannually by the Inverse Problems International Association, recognizes researchers under the age of 40 who have made significant advances in the mathematics of inverse problems; it was awarded to Bal at the 2011 Applied Inverse Problems Conference at Texas A&M University.

Inverse problems are about deciphering indirectly measured data of an unknown quantity, such as the inner structure of a patient. The aim is to go from an effect to the cause, as opposed to the simpler direct problem of going from cause to effect. In medical X-ray tomography, for example, the direct problem is to determine what kind of X-ray images (effect) we would get from different directions when imaging a patient whose inner structure (cause) we know. The inverse problem is the more difficult task of producing a three-dimensional reconstruction of the patient based on several two-dimensional X-ray images.

X-ray tomography is a linear inverse problem. For many medical measurements, by contrast, the body is probed with energy whose propagation depends on the medium, leading to nonlinear inverse problems. An example is electrical impedance tomography, which is based on feeding harmless electric currents into the body and reconstructing the inner conductivity distribution from the resulting voltages at the skin. The boundary measurements depend on the conductivity in a nonlinear way. Another example is the classic diagnostic method of manual palpation, which can be viewed as boundary measurements based on elastic deformations. Quite deep and interesting mathematics has been needed, and created, for the analysis of nonlinear inverse problems.

![image](https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-inverseproblem.jpg)

For Guillaume Bal, hybrid inverse problems, which often arise from nonlinear PDE models, are one of the most exciting areas of his recent work.

In recent years, Guillaume Bal has made a variety of mathematical contributions to the study of nonlinear inverse problems, concentrating for the most part on cases in which the propagation of the probing energy is modeled by partial differential equations. His studies cover a broad scientific domain, including integral geometry, direct and inverse transport models, Monte Carlo methods, asymptotic models for equations with random coefficients, and time-reversal imaging in random media. He has a special interest in hybrid inverse problems arising from coupled-physics measurements.

The solution of hybrid inverse problems is typically done in two steps. In the first, one solves an inverse boundary-value problem that provides high-resolution information about an internal structure. The internal functional revealed in this way can be viewed as another indirect measurement. The second step consists of solving the inverse problem of interpreting the latter data. The advantage of this procedure is that the second step would be extremely sensitive to measurement errors if the data were collected at the boundary; the virtually collected inner data allows a more stable solution and leads to better resolution.

Photo-acoustic tomography, or PAT, is a prime example of a hybrid inverse problem. In the first step, infrared light pulses are sent into tissue, leading to local thermal expansion at the sites of energy absorption. This rapid expansion creates ultrasound waves that can be detected when they arrive at the skin, allowing a high-resolution reconstruction of the distribution of optical energy absorption. In the second step, optical properties of the tissue are recovered from the internal information provided by the first step. Combining the high resolution of acoustic waves with the large contrast of optical waves, PAT is sometimes called the lightning-and-thunder method. Bal’s recent work has greatly advanced the understanding of the fundamental properties and possibilities of PAT.

   ■ ■ ■

In the inverse problems research community, Bal is known as an energetic mathematician whose enthusiasm is catching. In September 2011, during a conference in Edinburgh, I had the chance to interview him for SIAM News.

**Among mathematical disciplines, what is it about inverse problems in particular that drew you into the field?**

It all started when Oliver Dorn and I met as postdocs at Stanford and discussed the mathematics of inverse problems. Also, an important role was played by the MSRI theme year on inverse problems in 2001. I was working with a time-reversal problem related to transport equations, and the talks at a workshop in November 2001 revealed a variety of new and fascinating mathematical questions.

The main reason for my continuing interest is the fruitful interaction between applications and theory, which is a characteristic feature of inverse problems.

**What is the role of hybrid, or combined, imaging modalities among traditional methods?**

From the practical point of view, it is advantageous to combine two measurements, one having high contrast, the other high resolution. There are a bunch of candidates for practically useful hybrid imaging methods. Judging their potential is based on analyzing the strength of the physical interactions involved: Is there enough signal to yield information?

From the theoretical point of view, hybrid inverse problems lead to the study of so-called internal functionals. There are lots of open problems and new fundamental questions about them, so there is no lack of exciting research work to be done. On one hand, new tools are needed for analyzing these internal functionals, and on the other hand, some old tools are readily applicable. So both challenges and ways to proceed are available. 

(Warming to the topic, Bal continues his comments on hybrid inverse problems.)

The connection to the theory of nonlinear PDEs is interesting as well—traditionally, nonlinear inverse problems arise from linear PDE models, but in hybrid cases the models are often nonlinear.

A long-term research objective is to provide a comprehensive classification of inverse problems with internal functionals.

**Which one of your published results are you the most proud of?**

It’s really hard to pick out just one paper. I mean, could you pick one of yours? If I have to, it would be the article “Ray Transforms in Hyperbolic Geometry,” concerning nonlinear tomography in hyperbolic geometry, with applications to single-photon emission computed tomography (SPECT). There the tomographic reconstruction task is reduced to a Riemann–Hilbert problem.

Rather than promote a single paper, though, I would say that the recent activity on hybrid inverse problems is the most exciting cohesive work I’ve done in the field of inverse problems theory.

**How do you see the future of inverse problems?**

Well, new measurement techniques do create new questions all the time, and the theory of inverse problems provides tools for answering them. There will surely be a continuous feed of interesting problems offered by future technologies.

   ■ ■ ■
   
Guillaume Bal received a PhD at the University of Paris VI in 1997 under the supervision of Yvon Maday. For his PhD thesis, “Coupling of Equations and Homogenization in Neutron Transport,” he received the Jean-Pierre Lepetit Prize for the best PhD thesis defended in 1997–1998 at the Direction des Études et Recherches d’Electricité de France (EDF). He is currently a professor of applied mathematics at Columbia University.

Previous winners of the Calderón Prize were Matti Lassas (2007) and Martin Burger (2009). Lassas is known as a versatile mathematician who has provided innovative solutions to analytic and geometric inverse problems, to questions of invisibility, and to practical imaging problems, such as three-dimensional dental X-ray tomography. Martin Burger, a similarly multi-faceted mathematician, has created and analyzed reconstruction algorithms for medical imaging and image processing. He is an expert on the theory and application of sparsity-promoting inversion, such as total variation regularization and level set methods.