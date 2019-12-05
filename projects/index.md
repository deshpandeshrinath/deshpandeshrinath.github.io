---
layout: default
title: Projects
---
## Research Internship @ Autodesk AI and Robotics Lab
- CAD Informed Adaptive Robotic Assembly; Developed an Assembly Motion Planner Algorithm; Python plugin for Fusion 360
- Integrated a concave-concave mesh collision library (C++) with In-house Robotic Environment; Impacted three research projects
- Initiated a deep learning project on Representation Learning of Assembly Motion Plans; Developed a representation schema for Motion Plans; Trained a VAE on a synthetic dataset; Applications in Grasp Authoring, Qualitative Assessment of Motion Plans
- [5 minute Showcase Presentation]({{ "/assets/Showcase/index.html" | absolute_url }})

## Research Projects @ CAD Innovation and Engineering Lab
- ### Machine Learning
  - Representation Learning and Segmentation of mechanical motions; Trained motion classifiers for Type-Synthesis.
  - Developing Generative Models (Conditional GAN and VAE) for computational creativity and managing uncertainty.
  - Interactive ML Agent for Assisted Mechanism Design; Human Machine Collaboration; ML for conceptual machine design.
  - Working on deep RL model for Mechanical Design; Developed an OpenAI-gym Environment for Mechanism Design Task.
  - Developing a Machine Learning Driven Web-Based App for Synthesis of Mechanical Linkages; Deployed on Google Cloud Platform;  url: [http://motiongenpro.appspot.com/](http://motiongenpro.appspot.com/); [Tensorflow, React, Redux, MongoDB]

- ### Optimization
  - Developed Lagrange Optimization routine for four-bar linkage synthesis; Reduces constrained optimization into a polynomial system of equations.
  - Solved the system by groebner basis method; implemented using GIAC npm package on node.js server.
  - Lead Author of an award winning publication for solving practical synthesis problems (doi: 10.1115/1.4037801)

## Paper Implementations and Course Projects
- ### Deep Reinforcement Learning for Continuous Control Tasks
   ([https://github.com/deshpandeshrinath/deepDGP](https://github.com/deshpandeshrinath/deepDGP))
  - Implemented Deep DPG algorithm to learn continuous control policies
  - Compatible with all OpenAI-Gym environments.
  - Implemented Hindsight Experience Replay for learning goal-oriented tasks with sparse binary rewards.
  - [Demo1](https://www.youtube.com/watch?v=C5tIEuEycJY), [Demo2](https://www.youtube.com/watch?v=qU8Nd9lyxlw), [Medium Blog](https://medium.com/@deshpandeshrinath/how-to-train-your-cheetah-with-deep-reinforcement-learning-14855518f916)

- ### End-to-End Monocular Visual Odometry by Deep Learning
  ([https://github.com/sladebot/deepvo](https://github.com/sladebot/deepvo))
  - Built a deep Recurrent Convolutional Neural Network for pose estimation of a car
  - CNN was derived from pretrained FlowNet2.0
  - Trained and tested on KITTI visual odometry dataset (grayscale)
  - Supported by [Human Interaction Lab](http://hi.cs.stonybrook.edu/), Stony Brook.
  - [Demo]({{ "/assets/deepvo.gif" | absolute_url }})

- ### Computing Consensus Trajectory
  - Developed an algorithm to find valid representative trajectory among n time stamped trajectories; works for any dimensional space.
  - Algorithm builds a weighted DAG on input; designed heuristics for assigning weights.
  - Consensus Trajectory is the dijkstra's shortest path on DAG.

- ### Motion Planning and Optimal Control of a Car in Drifting Conditions
  - Designed Extended Kalman Filter for Observer; Modeled governing dynamics; Used empirical tire friction model for drift simulations.
  - Computed shortest path using Dynamic Programming. Obtained Optimal Control via Direct Collocation; Implemented in MATLAB using optimal control solver [GPOPS II](http://www.gpops2.com).
  - Used high gain PID controller to follow optimal control. Results match with empirical drifting techniques used by race drivers.
  - [Report]({{ "/assets/control-sys-project/Report.html" | absolute_url }})

- ### Motion Planning of Baxter Arm for Planar Pushing Task
  - Computed smooth B-Spline motion for pushing. Computed Jacobian matrix; Applied approximate Inverse Position Kinematics
  - Obtained joint angles and rates for the task. Performed simulations to validate the results.

- ### Interactive Manipulation of NURBS Surfaces
  - QT5, OpenGL based implementation in C++ for interactive manipulation of Non Uniform Rational B-Spline Surfaces.
