---
title: "KUKA youBot Mobile Manipulation"
author_profile: true
key: 5
excerpt: "Trajectory planning, Feedforward control"
header:
  teaser: /assets/images/449.gif
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

This project plans a trajectory for the end-effector of the youBot mobile manipulator (a mobile base with four mecanum wheels and a 5R robot arm), performs odometry as the chassis moves, and performs feedback control to drive the youBot to pick up a block at a specified location, carry it to a desired location, and put it down. 

## Video Demo
<iframe
    width="100%"
    height="50px"
    src="https://www.youtube.com/embed/UkNCx6J6GJc"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

## Reference Trajectory Generation
To start off, I wrote a function to generate the reference trajectory for the end-effector frame. This trajectory is consisted of 8 concatenated trajectory segments: 
 - Move the gripper from its initial configuration to a "standoff" configuration above the block.
 - Move the gripper down to the grasp position. 
 - Close the gripper.
 - Move the gripper back up to the "standoff" configuration
 - Move the gripper to a "standoff" configuration above the final configuration.
 - Move the gripper to the final configuration of the object
 - Open the gripper.
 - Move the gripper back to the "standoff" configuration.

## youBot Kinematics Simulation
To know where the chassis, the wheels, and the arm links are in the simulation, I wrote a function to simulate the kinematics of the youBot. This function takes in:
 - Current configuration of the robot
 - Wheels speeds and arm joint speeds
 - Timestep
 - Max angular speed of the arm joints and the wheels
And it will simulate the kinamatics according to odometry and outputs:
 - The new configuration of the robot after the timestep

## Feedforward Control
To calculate the control law, we need the current actual end-effector configuration X(q,θ), a function of the chassis configuration q and the arm configuration θ. The values (q,θ) come directly from the simulation results in the last section. In other words, assume perfect sensors.

The output of this part is the commanded end-effector twist expressed in the end-effector frame. To turn this into commanded wheel and arm joint speeds, we use the pseudoinverse of the mobile manipulator Jacobian Je(θ). 

## Source code
[Github repo](https://github.com/hang-yin/Mobile_Manipulation)