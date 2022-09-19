---
title: "Pen Challenge"
author_profile: true
key: 10
excerpt: "Computer vision, Robot manipulation, OpenCV, Python"
header:
  image: /assets/images/pen_challenge.jpg
  teaser: /assets/images/pen_challenge.jpg
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

This project aims at enabling the PincherX 100 Robot Arm to grab a pen that is held in front of it. 

## Vision pipeline
To help the PincherX 100 Robot Arm to grab a pen, we take advantage 
of the depth and color sensors in the Intel RealSense D435i camera. 
To locate a pen in the 3D space, we use the following pipeline:
1. Locate pen in 2D space using RGB image stream
2. Align depth map to the RGB image
3. Threshold the aligned image in the HSV color space to locate the pen
4. Filter the image with dilation and erosion operations to reduce noise
5. Find contours of the pen
6. Calculate the centroid of the pen   


Since now we know the centroid of the pen in 3D space, 
we can move on to the robot control pipeline. 

## Robot control
To grab the pen given its 3D coordinate in space (from the camera), 
we use open loop control to move the gripper towards the pen and grab it.

[Github repo](https://github.com/hang-yin/Pen_Challenge)