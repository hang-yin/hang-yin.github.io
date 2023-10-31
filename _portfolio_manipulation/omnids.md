---
title: "Human-Multirobot Collaborative Mobile Manipulation"
author_profile: true
key: 6
excerpt: "ROS2, haptics control"
header:
  teaser: /assets/images/omnids.gif
classes: wide
---

## Video Demo
<iframe
    width="100%"
    height="50px"
    src="https://www.youtube.com/embed/SEuFfONryL0"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

## Part I: Migration from ROS1 Melodic to ROS2 IRON

To take advantage of the new features ROS2 provide, we transitioned 14 ROS1 Melodic packages over to ROS2 Iron. Here are some of the key steps we took:

 - Adapting Source Code: Updated the original code to incorporate ROS2-specific libraries like rclcpp.
 - Build System Modification: Adjusted packages to ensure compatibility with the ROS2 build system and its accompanying tools.
 - Updating Definitions: Updated message, service, and action definitions to be in line with ROS2 requirements.
 - Parameter Definition Updates: We made changes based on the structural shift from ROS 1 to ROS 2. While ROS 1 parameters are tied to a central server facilitating runtime retrieval via network APIs, ROS 2 places parameters on a per-node basis, making them adjustable in real-time through ROS services.
 - Docker Environment: Set up a Docker environment integrated with Ubuntu 22.04 and ROS2, allowing for hardware testing.
 - Unit Test Compatibility: Revised unit tests for ROS2 compatibility. Notably, my partner did exemplary work in this area – you can view the specifics of our approach with the catch2 testing framework for ROS2 [here](https://github.com/ngmor/catch_ros2).
 - Remote Launch: This is an innovative ROS2 package that empowers users to remotely initiate nodes and launch files via SSH. You can view the work done by my partner on this [here](https://github.com/NU-MSR/launch_remote).

## Part II: Integrating ros2_control into Omnid
The motivation behind our venture into ros2_control integration can be distilled into two reasons:

 - Modularity with ros2_control:
 
 ros2_control lets users deconstruct robotic systems into more straightforward, swappable components. Termed as "hardware interfaces," these components provide a plug-and-play capability. This becomes particularly useful when there's a need to substitute a specific hardware module or modify a control algorithm without overhauling the entire system.

 - Dynamic Reconfigurability:
 
 The framework offers an array of tools that facilitate the dynamic loading, unloading, initiation, and cessation of controllers during runtime. Such dynamic adaptability proves invaluable during developmental phases, offering rapid iterations, and operational stages, adjusting to evolving conditions or tasks.

However, integrating ros2_control posed a significant challenge. Our existing system had abstracted the chassis control down to its embedded microcontroller. While our microcontroller responded directly to a twist command, ros2_control mandates direct hardware access to each motor's position, velocity, and effort control. Our workaround was to conceptualize the entire base as a singular joint, manipulated via three velocity interfaces: twist linear x, twist linear y, and twist angular z. Here's a diagram of our ros2_control architecture: 

![ros2-control-architecture]({{ site.url }}{{ site.baseurl }}/assets/images/omnid_ros2_control.png)

## Part III: End-to-End Imitation Learning for Human Assistive Assembly (In-progress)

Our prior work with omnids has empowered humans to collaborate seamlessly with robots, enabling effortless manipulation of sizable and weighty payloads through gravity compensation and passive compliance. Building on this, our current project aims to further simplify this co-manipulation process. We're adopting an imitation learning approach, inspired by the [ALOHA work](https://arxiv.org/abs/2304.13705), to better "infer" human intent. The objective is for the robot to autonomously apply supplementary forces on the end effectors, allowing humans to exert less effort.

Below is an architecture diagram illustrating the adapted Action Chunking with Transformers policy, inspired by the ALOHA paper:

![cvae-architecture]({{ site.url }}{{ site.baseurl }}/assets/images/omnid_cvae_architecture.png)

At this stage, our primary focus revolves around data collection and fine-tuning the model.

## Reference
 - Elwin, M. L., Strong, B., Freeman, R. A., & Lynch, K. M. (2023). Human-multirobot collaborative mobile manipulation: The Omnid Mocobots. IEEE Robotics and Automation Letters, 8(1), 376–383. [https://doi.org/10.1109/lra.2022.3226366](https://doi.org/10.1109/lra.2022.3226366)
 - Zhao, T. Z., Kumar, V., Levine, S., & Finn, C. (2023). Learning Fine-Grained Bimanual Manipulation with Low-Cost Hardware. arXiv preprint arXiv:2304.13705. [https://doi.org/10.48550/arXiv.2304.13705](https://doi.org/10.48550/arXiv.2304.13705)