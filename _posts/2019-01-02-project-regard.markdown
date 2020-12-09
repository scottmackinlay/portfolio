---
layout: post
title:  "Project Regard"
date:   2019-01-02 15:39:40
preview: /assets/regardSmall.png
---

![Picture 1]({{"/assets/regardHero.png"|absolute_url}})

Project Regard was an internal project at Synapse Product Development. The challenge: what's an efficient way to track the gaze of three people in a room? The status quo solution involves an absurdly high resolution camera, and similarly beefy image processing to handle the data. Our solution is two phase: one wide angle  camera to figure out where everyone is standing, and one telephoto camera that is pointed at each person's face in turn. The advantage of this solution is that neither camera need be exceptionally high resolution. 

This project focuses on the camera that gets pointed at everyone's faces. To be precise, it needs to flick between faces fifteen times per second. Instead of moving the whole camera, here's what it looks like if we just move the mirror:

![Picture 1]({{"/assets/regardDiagramPivot.png"|absolute_url}})

I developed a micro-mechatronic pivoting mechanism that uses a magnet and a flexural transmission in order to create a hysteresis-free, ultra lightweight, and high cycle count assembly. The mirror mount is a fiberglass composite to optimize for stiffness while keeping weight low. To ensure that this magnetic mount stayed attached, we ran the assembly through its paces when attached to a universal tester in order to characterize the forces anticipated by the pivot. 

![Picture 1]({{"/assets/regardTesting.jpg"|absolute_url}})

Here is what the system looked like after a few rounds of prototyping:

![Picture 1]({{"/assets/regardFlexure.png"|absolute_url}})

Unfortunately, the flexural transmission was failing to fatigue after a new thousand cycles. In order to improve performance, I reached out to experts and talked about all sorts of solutions:
* Changing material (1080, 1095, berylium copper, nytinol, etc)
* Custom heat treating to relieve stress in work hardened region
* Adapting the geometry to reduce stress risers

Ultimately, the solution involved a little of all three. I swapped out the rod spring for a coil configuration which was heavier, but could survive cycle counts well into the millions. 

![Picture 1]({{"/assets/regardPivot.png"|absolute_url}})

But was the added weight of the coil spring too much? To test this, I shot the following clip of a few different stiffnesses/lengths of spring at 1,000 fps with a high speed camera. Here, the settling times are exagerated immensely and I could comfortably say that the optimal coil spring resulted in a sufficiently quick settling time. 

![Picture 1]({{"/assets/springComparison.gif"|absolute_url}})

![Picture 1]({{"/assets/regardDiagram.png"|absolute_url}})

Callibrating this device was really cool. Basically, we are trying to convert between the 2-space of the linear actuator displacements to the 2-space of the camera view. The fastest way to create the transfer function between these spaces involved replacing the camera with a laser pointer and using openCV to track where the laser struck a gridded whiteboard. This way, any non-linearities in our flexural transmission can be callibrated out of the controls. 

