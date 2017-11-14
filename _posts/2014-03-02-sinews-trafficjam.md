---
layout: post
title: "[SIAM NEWS] Smells Like a Traffic Jam"
author: "李军"
categories: journal
tags: [siam, ca]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

By <u>Dana Mackenzie</u>

November 01, 2013

[Freelance writer Dana Mackenzie writes from Santa Cruz, California. He is the author of the 2012 book The Universe in Zero Words: The Story of Mathematics as Told Through Equations.]

Next time you’re at a picnic and you discover a procession of ants marching over your meal, wait just a second before you throw your hamburger into the nearest trash can. Take a moment to admire the rapid, purposeful flow of traffic on the ant highway. Pause to appreciate what you don’t see: stopped ants.

Now compare this ant highway to an interstate highway through any large American city at rush hour. Whether it’s Route 5 in Seattle or Route 95 outside Washington, DC, the story will be the same—long lines of stopped vehicles.

What gives? What do ants know that we don’t know? And more importantly, is there anything we can do to make our highways a little bit more like ant highways?

Those are some of the questions studied by Katsuhiro Nishinari, a self-described “jam-ologist” at the University of Tokyo, who spoke about traffic at this year’s SIAM Annual Meeting in San Diego. “Jam-ology is a very interdisciplinary study,” says Nishinari. “It extends not only to vehicles and ants but also pedestrians, schools of fish in the water, or inventory in a warehouse.”

Even the brain has some similarities to a traffic network, as another traffic expert points out. “They are both consensus-like systems with nearly identical equations,” says Sean Brennan of Pennsylvania State University. “I don’t think it’s a coincidence that the 1-dimensional shock-wave behavior of vehicle traffic jams is remarkably similar to the 2-dimensional neural behavior that manifests itself as seizures.”

Traffic engineers, physicists, biologists, and mathematicians have been modeling different kinds of traffic for more than 75 years, and they have come up with a wide variety of mathematical models. And yet, we still don’t have an answer even to some simple questions, such as: Can one person unblock a traffic jam?

Let’s get back to those ants. One of the main things that makes them different from humans is a specialized sense of smell. According to Nishinari, their ability to detect pheromones excreted by other ants gives them a way to estimate the density of ants in their immediate vicinity. Unlike humans at rush hour, ants won’t let the density exceed a critical level beyond which the flux of ants would start to decrease. Another thing they won’t do is pass one another. And they always maintain a safe following distance. As a result, they tend to form large platoons that move in a synchronized fashion to their goals. If humans adopted these three simple behaviors, we would be a long way toward curing our traffic woes.

**Technological Fixes for Selfish Humans**

Perhaps it’s hopeless to expect humans to behave this way—we’re just too selfish. Moreover, we have no incentive to change. If just one driver chose to obey these rules, it wouldn’t make any difference as long as other drivers continued in their normal selfish ways.

But technology can encourage us to behave more altruistically. Metering lights on highway entrance ramps are intended to keep the density of traffic below a critical level. High-occupancy vehicle lanes have the same purpose, along with another, less obvious benefit: They reduce the amount of lane-changing. According to Michael Cassidy, a civil and environmental engineer at the University of California at Berkeley, people often overlook this point. “Even if the special lane is underused, even if it’s only 60% filled, the net benefit to all traffic can be positive. There is less lane changing between the adjacent lanes, and that means less lane changing near the bottlenecks.” 

Another technological innovation just starting to show up on the world’s roads is automatic cruise control. Nishinari consulted on the development of a system called CyberNavi (sold by Pioneer Electronics in Japan, but not in the U.S.), that warns drivers when they get within 40 meters of the car ahead. More ambitious systems, already under development in Europe, will enable cars to “talk” to each other and to the infrastructure of the highway. Using wireless communication and GPS devices, cars will tell the highway where they are and what the conditions are around them. In turn, the highway will warn them of traffic jams up ahead, enabling them to slow down in advance. If everybody’s car has the technology, it will keep all the cars spaced far enough apart to give the jam a chance to dissipate. It’s the next best thing to ant pheromones.

You don’t have to wait, however, if a retired engineer and amateur scientist named Bill Beaty is right. In 1998, Beaty wrote the following Internet post about an impromptu experiment he had conducted on State Route 520 near Seattle:

“Rather than repeatedly rushing ahead with everyone else, only to come to a halt, I decided to try to move at the average speed of the traffic. I let a huge gap open up ahead of me, and timed things so I was arriving at the next ‘stop-wave’ just as the last red brakelights were turning off ahead of me.

“Finally I happened to glance at my rearview mirror. There was an interesting sight.

. . . In the neighboring lanes I could see maybe five of the traffic stop-waves. But in the lane behind ME, for miles, TOTALLY UNIFORM DISTRIBUTION. . . . By driving at the average speed of traffic, my car had been ‘eating’ the traffic waves.” [Emphasis present in original.]

Because his article was not published in a scientific journal, Beaty’s home-brewed experiment did not attract a lot of attention. Last year, though, Nishinari and three co-authors put “jam-absorption driving” to the test. In a simple computer model of a single-lane road, they confirmed that Beaty’s strategy works. “Slow-in, fast-out” driving, even by one driver, could give an already-formed jam time to dissolve and also prevent the creation of new jams behind the jam-absorbing driver. Beyond that, Nishinari and his colleagues showed (in work not yet published) that the total fuel consumption of all the vehicles on the highway would be decreased by as much as 35%. Thus, one person can make the driving experience more pleasant for everyone and benefit the environment.

**Jam-absorbing Drivers**

Before you go out and try to drive like Beaty, it’s important to be aware of certain caveats. First, the model Nishinari’s group used was extremely simplistic. The “fast-out” part of the model (which was not part of Beaty’s experiment) was actually instantaneous, which is both physically impossible and extremely unwise. Even if you could accelerate instantaneously, you would run into the car ahead of you unless it was doing the same thing. Also, the model did not take into account the likelihood that the big gap in front of a jam-absorbing driver would encourage drivers from other lanes to cut in front of him.

Other jam-ologists have differing opinions. “The ‘slow into a jam’ strategy is in complete accord with our prior work,” says Brennan. He and his student Kshitij Jerath have work in progress that leads to a similar conclusion, but with a catch. There appear to be “event horizons” such that a car outside the event horizon can eat the jam, although a car inside the event horizon cannot have any effect. Brennan also thinks, based on intuition rather than study, that a gap of more than 5 MPH between your speed and your neighbors’ speeds would lead to more accidents—which certainly would not solve the jam problem.

Cassidy, by contrast, is very skeptical of one car’s ability to affect a traffic jam. “The name of the game should be one thing and one thing only, maximizing discharge rate from your bottleneck,” he says. Because the “slow-in” phase doesn’t affect anything downstream of the bottleneck, he thinks that it cannot address the root of the problem.

Adaptive cruise control (ACC) should, in principle, be even better than manual “jam-absorption,” and it’s based on a similar principle—slowing down long in advance of the “event horizon.” But Brennan and Jerath have shown that a little bit of a good thing can actually turn out badly. They studied a traffic model with two populations of cars. The cars in one group, with a “sensitivity” of 0.3 to the actions of the car in front of them, would correspond to cars not equipped with automatic cruise control. The other group, with a sensitivity of 0.7, would be cars with ACC systems that could detect when the car in front was slowing down, and react accordingly.

When almost all the vehicles on the road had ACC, Brennan and Jerath showed that the highway could accommodate twice as much traffic before starting to jam. But the increased capacity came with a cost: The flow of traffic became highly vulnerable to the introduction of just a few non-ACC vehicles. If the number of ACC-equipped vehicles decreased from 95% to 90%, for instance, the road’s capacity would decrease significantly. If the density was already close to capacity when the non-ACC vehicles joined the flow, traffic would almost certainly jam. The result suggests that ACC-equipped vehicles should get a separate lane, if and when these systems become popular. But the lane restriction would need to be enforced very strictly.

Heterogeneous traffic (made up, say, of vehicles with and without ACC) is a headache not only for traffic but also for traffic modelers. A team led by Saskia Ossen of the Delft University of Technology recently showed that none of the seven leading traffic models predicted the behavior of heterogeneous traffic accurately, when compared to real data extracted from high-speed videos taken from a helicopter. The models include lots of parameters that describe the average behavior of drivers. But a highway where half the vehicles have sensitivity 1 and half have sensitivity 0 will behave very differently from a highway where all the vehicles have sensitivity 0.5. Now imagine a highway with buses, trucks, ACC-equipped vehicles, non-ACC-equipped vehicles . . . Or even worse, go to India, where pedicabs, motorcycles, and elephants are added to the mix.

**Investing in Pedestrian Traffic**

The elephants bring up a final interesting point. Though we usually think of traffic as a problem involving vehicles, some of the least-understood traffic problems involve pedestrians (of the two-legged variety). According to Tobias Kretz, a project manager for Viswalk, a pedestrian simulation developed by PTV in Karlsruhe, Germany, it’s partly a matter of cost. When you build a road, you’ll do a traffic simulation because the relative cost is small. That’s not true when you build a sidewalk. However, pedestrian flow becomes very important during major events like the Olympic Games. PTV has consulted with the organizers of the Vancouver, London, and Rio de Janeiro Olympics to get fans to their desired events faster.

Because the behavior of pedestrians has been studied much less than that of vehicles, Kretz had to develop his own simulations from the ground up. This year, though, a group of researchers led by Frank Fiedrich of Wuppertal University conducted experiments with 1000 pedestrians to see how they behaved when forced to go around corners or when funneled through a narrow entrance. Kretz looks forward to comparing his models to the group’s field data.  

<figure class="half">
	<img src="https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-trafficjam-1.jpg">
	<img src="https://github.com/brucejunlee/brucejunlee.github.io/raw/master/assets/img/siam-trafficjam-2.jpg">
</figure>     

In this experiment conducted in 2013 in Dusseldorf, pedestrians in encoded hats round a corner. The experiments were intended to provide data on how traffic jams form in pedestrian traffic. The first few pedestrians travel unimpeded around a corner (left). Later, a wave of congested traffic forms in advance of the corner and the velocity of the pedestrians through the corner decreases. Photos courtesy of Forschungszentrum Jülich/Ralf Eisenbach. 

It may not be obvious, but research on pedestrian traffic is important for automobile traffic, too. According to the Downs–Thompson paradox, travel times in a big city tend to an equilibrium at which all methods of transportation will get you to your destination in the same time. Therefore, the transportation system is only as strong as its weakest link. If societies invest more in road traffic but neglect public transportation or pedestrian traffic, the result may be increased travel times. “We will just blow up the area extent of our cities, implying longer trip length, implying more people choosing the car instead of cycling or walking,” Kretz says. “If we invest in pedestrian traffic, cycle paths, and comfortable walking routes, the spiral will go the other direction.” For this reason, Kretz is skeptical of technological improvements like adaptive cruise control, special lanes, or adaptive speed limits. “I doubt that road jams can be prevented with measures for road traffic only. What we need is innovation in walking, cycling, and public transport.” 

--

**What’s in a Model?**

The earliest traffic models described traffic as a fluid with no individual cars. Such models are called macroscopic, because they depend only on large-scale variables, such as the average density and velocity of traffic. One valuable insight provided by these models is the fundamental diagram, which conveys the important information that on any road the flux of traffic (i.e., the velocity times the density) increases only up to a certain density, and then it starts to decrease. This is, in a nutshell, why jams occur. 

Unfortunately, fluid models have certain undesirable features. They predict that traffic jams should travel in either direction from a bottleneck; in practice, though, jams travel in only one direction: upstream. Fluid models also tend to have a rather unrealistic fundamental diagram. Empirical data show that at high densities, traffic enters a synchronized state in which all the cars travel at almost the same velocity. As soon as a disturbance happens (for example, one driver hits the brakes), the synchrony is broken and the flux drops, creating a “phantom traffic jam,” i.e., one with no visible cause, such as an accident or bottleneck. The very existence of two equilibrium states—one stable and the other metastable—violates a central tenet of the basic fluid models.

In recent years, traffic modelers have turned more toward microscopic models, which simulate every single car. Cellular automaton models are discrete in both time and space, representing the road as a row of cells that cars move into and out of at each time step. The most realistic class of models attempts to describe drivers’ actual behavior—representing the rate at which they accelerate as a function of the headway (distance between cars) or any other variables the modeler deems relevant. These models lead to huge systems of differential equations, either deterministic or stochastic, with as many variables as vehicles on the road. Another drawback of microscopic models is that the difficulty of acquiring experimental data on individual drivers makes all such models somewhat speculative.