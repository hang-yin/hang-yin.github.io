---
title: "Robot Jenga Assistant"
author_profile: true
key: 1
excerpt: "ROS2, MoveIt, OpenCV, Machine Learning"
header:
  teaser: /assets/images/jenga.gif
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

This project is meant to turn a Franka Emika Panda arm into a Jenga assistant! It uses computer vision to detect Jenga bricks and place them on top of the tower. The robot plans and executes trajectories using a custom MoveGroup API.

## Video Demo
<iframe
    width="100%"
    height="50px"
    src="https://www.youtube.com/embed/aCotjAaHfwM"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

## Calibration

 - Calibrating the robot relies on adding frames to the tf tree based on known geometry. 
 - The robot is sent to a calibration position, then given an april tag that aligns with the gripper frame. 
 - Once the camera can see the tag, it creates series of transforms from the camera to the tag and finally to the base of the robot. 
 - Calibration pose: 

![Calibration Pose]({{ site.url }}{{ site.baseurl }}/assets/images/jenga-calibration.png)

## Tower Detection

 - We detect the tower using the depth image from an Intel Realsense camera. 
 - Once the top of the tower and the table are found by generating contours on the depth image, we repeatedly scan between these locations looking for partially removed pieces. 
 - The starting orientation of the tower is determined through line detection in OpenCV. 

![Tower Detection]({{ site.url }}{{ site.baseurl }}/assets/images/jenga-tower-detection.png)

## Machine Learning for Hand Detection

 - Overview:
   - We performed transfer learning on a deep neural network to help us detect whether there are hands in the scene so that the robot knows when it should look for a Jenga brick. 
 - Dataset:
   - Video samples of the Jenga tower were taken and separated into two classes: with hand(s) and without hand(s) around. 
   - 1000 images were extracted from each class. 
 - Model: 
   - We performed transfer learning on a pretrained neural network - MobileNets
   - The MobileNet we are using implements depth-wise separable convolutions to build light weight deep neural networks
   - We only train the last layer of the MobileNet to perform our specific task
 - Training:
   - Epochs: 50
   - Batch Size: 16
   - Learning Rate: 0.001

## Custom MoveIt Library
 - Overview:
   - This package allows us to move our robot around while also avoiding objects by using different services. 
 - GetCartesianPath:
   - Moves the end-effector gripper in a straight line from start to end.
   - Uses multiple intermediate waypoints to ensure straight path.
 - GetPositionIK:
   - Calculates possible joint positions of robot from a given start and end position and orientation for the end-effector.
   - Used to Orient the gripper without shifting the position .
   - Used to move the robot when straight movement is not necessary.   
 - GetPlanningScene:
   - The environment around the robot.
   - This allows us to add in the table, camera, and jenga tower to avoid collisions .

![MoveIt Visual]({{ site.url }}{{ site.baseurl }}/assets/images/jenga-moveit.png)




## Source code
[Github repo](https://github.com/hang-yin/Jenga-Assistance)

## Reference
 - Howard, A., Zhu, M., Chen, B., Kalenichenko, D., Wang, W., Weyand, T., Andreetto, M., & Adam, H. (2017). MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications. [https://doi.org/10.48550/ARXIV.1704.04861](https://doi.org/10.48550/ARXIV.1704.04861) 

## Group members
Hang Yin, Katie Hughes, Liz Metzger, Alyssa Chen