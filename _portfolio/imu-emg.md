---
title: "IMU Controlled Robot Arm and EMG controlled Gripper"
author_profile: true
key: 10
excerpt: "C, Embedded System, IMU, EMG"
header:
  teaser: /assets/images/imu-emg.jpg
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

This project uses an Inertial Measurement Unit (IMU) to control the pose of a 2-jointed robotic arm. The end effector of this arm is a mechanical gripper controlled with an Electromyography muscle sensor (EMG).

## Video Demo
<iframe
    width="100%"
    height="50px"
    src="https://www.youtube.com/embed/lZlIVSBJQCs"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

## Components
 - Microprocessor: Microbit v2
 - Input
   - IMU (InvenSense ICM-20948 9-DoF)
   - Capacitive touch sensor (AT42QT1011)
   - EMG (MyoWare Muscle Sensor)
   - Force-Sensitive Resistor (Interlink 402)
 - Output
   - Servo control board (PCA9685)
   - Servos (DS3218 MG, MG996R)

## Source code
[Github repo](https://github.com/hang-yin/IMUnipulator)

## Group members
Hang Yin, Nick Morales, Felipe Jannarone, James Oubre, Katie Hughes, David Dorf