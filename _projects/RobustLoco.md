---
layout: page
title: RobustLoco 
description: Benchmarking Robust Learning-Based Locomotion Under Severe External Disturbances
img: assets/img/RobustLoco.png
importance: 2
category: supporting projects
related_publications: false
---

**Motivation**

I benchmark popular methods for learning robust humanoid locomotion under extreme disturbances, particularly external forces and torques. Reliable low-level locomotion is crucial for high-level tasks such as loco-manipulation. For example, a high-level planner may generate target velocities, and poor low-level velocity tracking—especially under interaction forces from manipulated objects—can significantly degrade overall task performance.

**Experimental setups**

I utilized the Adversarial Motion Prior (AMP) training pipeline provided by the [TienKung-Lab repository](https://github.com/Open-X-Humanoid/TienKung-Lab/tree/main), which uses IsaacSim for simulation. The primary objective of this project was to reproduce several popular methods, as described below, and to report comparative results in the context of robust humanoid locomotion.

In this work, I investigated three widely used approaches:

(1) _Domain Randomization (DR)_: The policy is trained with domain randomization over key physical parameters, including the base mass, the centers of mass of all robot bodies, and terrain friction. In addition, random external forces and torques are applied at the base center of mass.

(2) _Concurrent State Estimation (CSE)_ [1]: The actor and critic are trained concurrently with a state estimator that infers critical states—such as velocities, foot height, and external forces and torques acting on the robot’s CoM—from a history of observations. These estimated states are concatenated with proprioceptive inputs and fed to the actor to improve robustness.

(3) _Rapid Motor Adaptation (RMA)_ [2]: A student–teacher framework in which the student policy learns to adapt online by inferring latent dynamics information provided by a privileged teacher during training.

**Results**

Figure 1 shows the velocity tracking performance and transport cost of the validated methods. From the figure, it can be seen that the student policy generally performs best among the three methods. CSE shows no significant improvement over naive DR, and even performs worse in some cases.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/RobustLoco_materials/vx.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/RobustLoco_materials/wz.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/RobustLoco_materials/CoT.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Figure 1. (Left) Forward velocity tracking in x direction (Middle) Angular velocity tracking (Right) Cost of Transport  
</div>

The following [video](https://www.youtube.com/watch?v=SRodEnhhWaE) illustrates the policy obtained using the CSE method, which enables the robot to run uphill under an external force disturbance of −40 N while tracking a velocity command of 1 m/s.

**References**

[1] G. Ji, J. Mun, H. Kim and J. Hwangbo, "Concurrent Training of a Control Policy and a State Estimator for Dynamic and Robust Legged Locomotion," in IEEE Robotics and Automation Letters, vol. 7, no. 2, pp. 4630-4637, April 2022, doi: 10.1109/LRA.2022.3151396.

[2] A. Kumar, Z. Fu, D. Pathak, and J. Malik, “RMA: Rapid Motor Adaptation for Legged Robots,” in Proceedings of Robotics: Science and Systems (RSS), 2021.


