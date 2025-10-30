---
title: "Emergent Behavior in Multi-Robot Swarms"
author_profile: true
toc: true
key: 8
category: "Perception & Navigation"
excerpt: "Distributed control, state machine, Docker, Python"
description: "Implemented two distributed control algorithms that create complex emergent behaviors from simple local rules. The first mimics the Brazil nut effect to spatially segregate robots by size without centralized coordination. The second replicates Reynolds' flocking behavior—separation, alignment, and cohesion—to produce bird-like group movement. Each robot runs identical control code and makes decisions based only on nearby neighbors, yet the swarm exhibits sophisticated collective patterns. Built with Docker for easy simulation deployment, this project showcases how decentralized systems can achieve coordination that would be fragile or impossible with centralized control."
header:
  teaser: /assets/images/swarm-tn.png
classes: wide
---

{% comment %} 
sidebar:
  - title: "Role"
    image: http://placehold.it/350x250
    image_alt: "logo"
    text: "Designer, Front-End Developer"
  - title: "Responsibilities"
    text: "Reuters try PR stupid commenters should isn't a business model"
{% endcomment %} 

Implementation of two swarm algorithms: brazil nut effect spatial sorting and Reynolds flocking. 

## Brazil nut effect spatial sorting
![Brazil-nut]({{ site.url }}{{ site.baseurl }}/assets/images/brazil-nut.jpg)

Brazil Nut Effect is the phenomenon that in a cereal packs under vibration, the largest particle, which is usually the Brazil nut, will end up at the top. Based on this kind of segregation pattern, it can be applied to the task of sorting a swarm and multi-robot system based on the artificial size assigned to the robots. 

This project implements the algorithm described in "Segregation in Swarms of e-puch Robots Based on the Brazil Nut Effect" by Chen et al.

### Control
The motion of each robot is governed by the following three forces:
1. Attraction towards a point common to all robots, which emulates the effect of a gravitational pull. 
2. Random motion, which emulates the effect of vibration. 
3. Repulsion from nearby robots, which emulates the effect of collisions. 

## Reynolds flocking
![flocking]({{ site.url }}{{ site.baseurl }}/assets/images/flocking.jpg)

Reynolds flocking is a computer model invented by Craig Reynolds in 1986. It aims for simulating the coordinated motion of large number of animals such as bird flocks and fish schools. 

This project implements the algorithm described in "Reynolds flocking in reality with fixed-wing robots: communication range vs. maximum turning rate" by Hauert et al.  

### Control
Each robot is steered by changing their turn rate proportionally to the error between their current heading and their desired heading. The desired heading is given by the weighted sum of the following vectors: 
1. Alignment: mean velocity of all robots within communication range.
2. Cohesion: vector pointing towards the center of mass of all robots within communication range
3. Separation: each robot within the communication range generates a repulsion vector that is inversely proportional to the distance separating the two robots. These vectors are then summed and the resulting vector is normalized. 
4. Migration: vector pointing towards the migration point. 

## Source Code
Since this is a class project, the source code can not be provided for now. 

## References
- [Segregation in Swarms of e-puch Robots Based on the Brazil Nut Effect](https://dl.acm.org/doi/10.5555/2343576.2343599)
- [Reynolds flocking in reality with fixed-wing robots: communication range vs. maximum turning rate](https://ieeexplore.ieee.org/document/6095129)