---
layout: post
title:  "Slow Screen"
date:   2015-10-09 15:39:40
preview: /assets/slowScreenSmall.jpg
youtubeId: t1mdSVDZvLI

---

{% include youtubePlayer.html id=page.youtubeId %}

What can a mechanical screen look like? If you have 835 servos, a few thousand dollars, and no deadline you can make something like [a wooden mirror](https://www.youtube.com/watch?v=BZysu9QcceM&t). But what if you only have __5 servos, a hundred dollars, and two months?__ With those constraints, can we still make an engaging mechanical screen? The answer is yes; but unlike other screens, ours has a framerate of about .01 fps and so it is called Slow Screen.

The trick to getting N actuators to control N<sup>2</sup> elements is by taking advantage of our system's characteristic frequency response. Each "pixel" is a mass that is connected to its vertical neighboring pixels by a torsional spring, the top spring is fixed, and the bottom spring is controled by a servo. Using recessed LED strips, when the pixels are angled to the left they appear red, and when they are angled to the right, they appear blue. So, with the right driving signal, we can control the positions and velocities of every pixel and display (low res) images on our screen.

How did we find the correct diving frequency? Iteratively. It would have been real hard to start by trying to control five masses, so we started with one:

![Picture]({{"/assets/singleMass.png"|absolute_url}})

Using __computer vision__, we tracked the behavior of a single pixel and taught our code until it could predict its motion perfectly. Once we could predict its velocity based on a given driving frequency, we stepped up to two masses, then three, and then five. At each step, we made the best prototype we could, and tested it rigorously to ensure that we didnt accumulate bugs as we scaled up in complexity. Once we created an accurate mathematical model of our system, we wrote some __20-dimensional gradient descent that allowed our program to discover the optimal driving frequency__ for a desired state of positions and velocities. 

![Picture]({{"/assets/slowScreenTest.png"|absolute_url}})

The technical problem of discovering driving frequencies wasnt the only thing that we tackled iteratively. In addition, the physical appearance of this piece underwent a lot of redesign. Here are some preliminary renders of ideas that we considered for the appearance of the pixels:

![Picture]({{"/assets/slowScreenProto1.gif"|absolute_url}})

![Picture]({{"/assets/slowScreenProto2.gif"|absolute_url}})

A huge shoutout to my two other team members, Ezra Johnson and Max Schommer; and to Chris Lee the professor and friend who believed in us when the other faculty called us crazy for undertaking such an ambitious project.