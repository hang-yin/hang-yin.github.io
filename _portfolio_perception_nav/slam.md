---
title: "Feature-based EKF-SLAM from Scratch"
author_profile: true
toc: true
key: 0
excerpt: "Extended Kalman Filter, Localization, Simulation, C++"
header:
  teaser: /assets/images/slam_gif.gif
---

## Video Demo
<iframe
    width="100%"
    height="50px"
    src="https://www.youtube.com/embed/6bvgkD7kn_s"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

## Simulation Environment from Scratch

For this project, a simulation environment was created using ROS2 and Rviz as a visualization tool. A ROS2 node was developed to simulate robot position and landmarks to test various components of this project, including the EKF SLAM algorithm and landmark detection. Collision detection between the simulated robot and obstacles was also implemented.

![Simulated environment]({{ site.url }}{{ site.baseurl }}/assets/images/slam-simulation.png)

## Kinematics and 2D Rigid Body Transformations

Throughout the project, helper libraries were developed in C++ to handle calculations related to differential drive kinematics, 2D rigid body transformations, and other tasks. These libraries can be found in the turtlelib directory of the repository.

## Extended Kalman Filter SLAM

The primary component of this project is the implementation of feature-based extended Kalman filter simultaneous localization and mapping ([EKF-SLAM](https://www.cs.unc.edu/~welch/media/pdf/kalman_intro.pdf)). The EKF-SLAM algorithm consisted of three steps: initialization, prediction, and update. At each timestep, odometry and sensor measurements were used to estimate the state of the robot and landmarks. The prediction step updated the estimate of the full state vector and propagated uncertainty using the linearized state transition model. The update step involved computing the theoretical measurement given the current state estimate, the Kalman gain, the posterior state update, and the posterior covariance.

![EKF SLAM]({{ site.url }}{{ site.baseurl }}/assets/images/slam-ekf.gif)

## Landmark Detection

To detect cylindrical landmarks, laser scan data was processed using a machine learning approach that combined unsupervised (lidar point clustering) and supervised (circular regression) learning. The resulting clusters were filtered using a [circle-fitting algorithm](https://projecteuclid.org/journals/electronic-journal-of-statistics/volume-3/issue-none/Error-analysis-for-circle-fitting-algorithms/10.1214/09-EJS419.full) to eliminate false positives.

![Landmark detection]({{ site.url }}{{ site.baseurl }}/assets/images/slam-circle.png)

## Source code
To be posted. 

## Reference
 - Ali Al-Sharadqah. Nikolai Chernov. "Error analysis for circle fitting algorithms." Electron. J. Statist. 3 886 - 911, 2009. https://doi.org/10.1214/09-EJS419