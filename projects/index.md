---
layout: default
title: Projects
---
## Research Projects @ CAD Innovation and Engineering Lab
- ### Machine Learning
  - Developing Generative Models (VAE's and Auto-regressive RNN's) for computational creativity and conceptual machine design.
  - Working on deep RL model for Mechanical Design; Developed an OpenAI-gym Environment for Mechanism Design Task.
  - Variational autoencoders for representation learning of Linkage Trajectories; Trained classifiers for Mechanism Type-Synthesis

- ### Optimization
  - Developed Lagrange Optimization routine for four-bar linkage synthesis; Reduces constrained optimization into a polynomial system of equations.
  - Solved the system by groebner basis method; implemented using GIAC npm package on node.js server.
  - Lead Author of an award winning publication for solving practical synthesis problems (doi: 10.1115/1.4037801)

- ### MotionGen: Web, iOs and Android App for Linkage Synthesis
  - Developed smart-synthesis, motion interpolation functionalities for the cross platform app based on MVC architecture; [http://cadcam.eng.sunysb.edu/](http://cadcam.eng.sunysb.edu/)
  - Used Apache Cordova framework for iOs and Android implementations.

## Paper Implementations and Course Projects
- ### Deep Reinforcement Learning for Continuous Control Tasks
   ([https://github.com/deshpandeshrinath/deepDGP](https://github.com/deshpandeshrinath/deepDGP))
  - Implemented Deep DPG algorithm to learn continuous control policies
  - Compatible with all OpenAI-Gym environments.
  - Implemented Hindsight Experience Replay for learning goal-oriented tasks with sparse binary rewards.

- ### End-to-End Monocular Visual Odometry by Deep Learning
  ([https://github.com/sladebot/deepvo](https://github.com/sladebot/deepvo))
  - Built a deep Recurrent Convolutional Neural Network for pose estimation of a car
  - CNN was derived from pretrained FlowNet2.0
  - Trained and tested on KITTI visual odometry dataset (grayscale)
  - Supported by [Human Interaction Lab](http://hi.cs.stonybrook.edu/), Stony Brook.

- ### Computing Consensus Trajectory
  - Developed an algorithm to find valid representative trajectory among n time stamped trajectories; works for any dimensional space.
  - Algorithm builds a weighted DAG on input; designed heuristics for assigning weights.
  - Consensus Trajectory is the dijkstra's shortest path on DAG.

- ### [Motion Planning and Optimal Control of a Car in Drifting Conditions]({{ "/assets/control-sys-project/Report.html" | absolute_url }})
  - Designed Extended Kalman Filter for Observer; Modeled governing dynamics; Used empirical tire friction model for drift simulations.
  - Computed shortest path using Dynamic Programming. Obtained Optimal Control via Direct Collocation; Implemented in MATLAB using optimal control solver [GPOPS II](http://www.gpops2.com).
  - Used high gain PID controller to follow optimal control. Results match with empirical drifting techniques used by race drivers.

- ### Motion Planning of Baxter Arm for Planar Pushing Task
  - Computed smooth B-Spline motion for pushing. Computed Jacobian matrix; Applied approximate Inverse Position Kinematics
  - Obtained joint angles and rates for the task. Performed simulations to validate the results.

- ### Interactive Manipulation of NURBS Surfaces
  - QT5, OpenGL based implementation in C++ for interactive manipulation of Non Uniform Rational B-Spline Surfaces.
