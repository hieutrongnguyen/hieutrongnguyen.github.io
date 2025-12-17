---
layout: page
title: DO-CBF-QP
description: A Disturbance-Observer based Safety-Critical Control for Uncertain Affine Nonlinear Systems
img: assets/img/Control_System_for_Thesis_resized.png
importance: 2
category: major projects
related_publications: false
---

Quadratic programming based controller using control Lyapunov functions and control barrier functions (CBFs) are powerful method for multi-objective control problems. However, when applied to real-world scenarios, the presence of uncertainties and external disturbance can deteriorate the control performance. In this paper, this issue is tackled by using a disturbance observer (DO). The DO is designed based on the main principle of solving an optimization problem to minimize the approximation error. Both the DO and the controller are based on the nominal model of the system, but the overall system can handle the potential uncertainties and unknown disturbance in practical scenarios. Stability of the closed-loop system is analyzed and the effectiveness of the proposed controller is verified through numerical simulation. Compared to the state-of-the-art method ([L1 adaptive CBF](https://hybrid-robotics.berkeley.edu/publications/ACC2022_L1_Adaptive_CBF.pdf) approach), our controller can handle a more significant level of model uncertainties while requiring much less computation time.

The work has been published on the International Journal of Control, Automation and System, 2025 ([IJCAS](https://link.springer.com/article/10.1007/s12555-024-0918-9)). The implementation, including the L1-CBF framework as a baseline, is available on my [Github](https://github.com/hieutrongnguyen/DO-CBF-QP).