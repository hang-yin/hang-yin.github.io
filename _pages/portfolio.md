---
title: ""
layout: home
permalink: /
classes: wide
redirect_from:
  - /portfolio/
  - /portfolio
---

## About Me

I'm a Software Engineer at the [Stanford Vision & Learning Lab](https://svl.stanford.edu/), where I focus on robotics research. My work centers on developing 3D robot simulations and curating datasets to advance robot learning.

## Professional Experience
<table>
  <tbody>
    <tr>
      <td style = "border-bottom-width:0;"><img src="{{site.baseurl}}/assets/images/sail.png" alt="stanford" width="60"></td>
      <td style = "border-bottom-width:0;">
        <strong>Stanford AI Lab</strong> <br> 01/2024 - present <br> Software Developer 2</td>
      <td style = "border-bottom-width:0;"><img src="{{site.baseurl}}/assets/images/johnson-and-johnson.png" alt="j&j" width="60"></td>
      <td style = "border-bottom-width:0;">
        <strong>Johnson & Johnson</strong> <br> 06/2023 - 09/2023 <br> Robotics & Controls</td>
      <td style="border-bottom-width:0;"><img src="{{site.baseurl}}/assets/images/delta-lab.png" alt="nu" width="60"></td>
      <td style="border-bottom-width:0;">
        <strong>Northwestern Delta Lab</strong> <br> 03/2021 - 06/2022 <br> Research Assistant</td>
    </tr>
  </tbody>
</table>

## Education
<table>
  <tbody>
    <tr>
      <td style="border-bottom-width:0;"><img src="{{site.baseurl}}/assets/images/northwestern.jpg" alt="nu" width="60"></td>
      <td style="border-bottom-width:0;">
        <strong>Northwestern University</strong> <br> 09/2022 - 12/2023 <br> M.S. in Robotics
      </td>
      <td style="border-bottom-width:0;"><img src="{{site.baseurl}}/assets/images/northwestern.jpg" alt="nu" width="60"></td>
      <td style="border-bottom-width:0;">
        <strong>Northwestern University</strong> <br> 09/2019 - 06/2022 <br> B.S. with honors in Computer Science, <em>summa cum laude</em>
      </td>
    </tr>
  </tbody>
</table>


## Research

<div class="container">
  <div class="image-container">
    <a href="https://behavior.stanford.edu/challenge/">
      <img src="{{site.baseurl}}/assets/images/behavior_challenge.png" alt="behavior-challenge">
    </a>
  </div>
  <div class="text-container">
    <div class="header-row">
      <a href="https://behavior.stanford.edu/challenge/" class="title-link">
        <h3>BEHAVIOR Challenge: 50 full-length household tasks with 1200+ hrs of human teleoperation data</h3>
      </a>
    </div>
    <div class="text-content">
      <p>The BEHAVIOR Challenge at NeurIPS 2025 invites researchers to tackle long-horizon, everyday household tasks in realistic virtual home environments, supported by a large dataset of 10,000 richly annotated expert trajectories (over 1,200 hours) to advance robot planning and control in complex, human-centric settings.</p>
    </div>
  </div>
</div>

<div class="container">
  <div class="image-container">
    <a href="https://momagen.github.io/">
      <img src="{{site.baseurl}}/assets/images/momagen.png" alt="momagen">
    </a>
  </div>
  <div class="text-container">
    <div class="header-row">
      <a href="https://momagen.github.io/" class="title-link">
        <h3>MoMaGen: Generating Demonstrations under Soft and Hard Constraints for Multi-Step Bimanual Mobile Manipulation</h3>
      </a>
    </div>
    <div class="text-content">
      <p>MoMaGen automatically generates diverse training datasets for bimanual mobile manipulation by solving constrained optimization problems that ensure robot reachability and camera visibility from minimal human demonstrations.</p>
    </div>
  </div>
</div>

<div class="container">
  <div class="image-container">
    <a href="https://behavior-robot-suite.github.io/">
      <img src="{{site.baseurl}}/assets/images/brs_hardware.jpg" alt="brs">
    </a>
  </div>
  <div class="text-container">
    <div class="header-row">
      <a href="https://behavior-robot-suite.github.io/" class="title-link">
        <h3>BEHAVIOR Robot Suite: Streamlining Real-World Whole-Body Manipulation for Everyday Household Activities</h3>
      </a>
    </div>
    <div class="text-content">
      <p>We introduce the BEHAVIOR Robot Suite (BRS) for household mobile manipulation, featuring a bimanual wheeled robot with 4-DoF torso that achieves critical capabilities in coordination, navigation, and reachability. Our framework includes a cost-effective teleoperation interface and novel algorithm for learning whole-body visuomotor policies.</p>
    </div>
  </div>
</div>

<div class="container">
  <div class="image-container">
    <a href="https://behavior.stanford.edu">
      <img src="{{site.baseurl}}/assets/images/b1k.jpg" alt="b1k">
    </a>
  </div>
  <div class="text-container">
    <div class="header-row">
      <a href="https://behavior.stanford.edu" class="title-link">
        <h3>BEHAVIOR-1K: A Human-Centered, Embodied AI Benchmark with 1,000 Everyday Activities and Realistic Simulation</h3>
      </a>
    </div>
    <div class="text-content">
      <p>BEHAVIOR-1K is a comprehensive simulation benchmark for human-centered robotics with 1,000 real-world tasks. Powered by NVIDIA's Omniverse, it features diverse scenes, objects, and activities with realistic rendering and physics simulation. This benchmark aims to advance embodied AI and robot learning research.</p>
    </div>
  </div>
</div>

## Past Projects

{% assign sorted_portfolio = site.portfolio | sort: 'key' %}
{% for item in sorted_portfolio %}
<div class="container">
  <div class="image-container">
    <a href="{{ item.url | relative_url }}">
      <img src="{{ item.header.teaser | relative_url }}" alt="{{ item.title }}">
    </a>
  </div>
  <div class="text-container">
    <div class="header-row">
      <a href="{{ item.url | relative_url }}" class="title-link">
        <h3>{{ item.title }}</h3>
      </a>
    </div>
    <div class="text-content">
      <p>{{ item.description }}</p>
    </div>
  </div>
</div>
{% endfor %}

<style>
.container {
  display: flex;
  margin-bottom: 10px;
  gap: 10px;
}

.image-container {
  flex: 0 0 200px;
  height: 100px;
  overflow: hidden;
}

.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  display: block;
  transition: opacity 0.2s;
}

/* Special handling for logo-style images in the experience/education tables */
table img {
  width: 60px;
  height: 60px;
  object-fit: contain;
}

.image-container img:hover {
  opacity: 0.8;
}

.text-container {
  flex: 1;
  display: flex;
  flex-direction: column;
  min-height: 100px;
  justify-content: flex-start;
}

.header-row {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 0.25rem;
}

.header-row h3 {
  margin: 0;
  font-size: 0.8rem;
  color: #333;
  transition: color 0.2s;
  line-height: 1.2;
}

.title-link {
  text-decoration: none;
  color: inherit;
}

.title-link:hover h3 {
  color: #0066cc;
  text-decoration: underline;
}

.text-content p {
  margin: 0;
  font-size: 0.6rem;
  line-height: 1.4;
  color: #666;
}
</style>