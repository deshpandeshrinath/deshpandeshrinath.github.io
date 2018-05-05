---
layout: post
title: "Survey of Mechanism Design and Synthesis using Database or AI Methods"
date: 2018-01-30
mathjax: true
---
Mechanical devices will be important for the realization of motions in spite of an increasing application of electronically controlled direct drives.
Modern technologies like nanotechnology or biomechatronics open up new areas of application for mechanisms.
Therefore, the relevance of mechanism theory even increases. Current research and development activities are indicators for this trend.
Examples are mechanisms with several drives, parallel and serial structures, compliant elements, mechanisms to control high precision, large amount of mass inertia, complex spatial and coupled movements or mechanisms for miniature and micro assemblies. ([Taken from Application of computational kinematics in the digital mechanism and gear library DMG-Lib](https://www.sciencedirect.com/science/article/pii/S0094114X06000723).)


## Methods based on Shape optimization of the Coupler Path
* ### [Ullah and Kota]({{ "/assets/data-driven-synthesis/ullah1997.pdf" | absolute_url }}) have developed a method for shape comparison of closed planar curves.
The method calculates on Cumulative Angular Deviant function which is
independent of scale and rotation.
Fourier descriptors of this periodic function are used for shape comparison by
means of Fourier Deviant function.
This comparison function is used as objective function of optimization problem
formulated with the goal of linkage synthesis.

Here are some comments on the above approach:

1. The method is defined only for closed planar curves.
  - Although one could apply it to planar open curves, method is affected by
    selection of starting point.
2. Fourier Deviant function combines amplitude and phase deviations of Fourier
   descriptors, which is a parameter to be set by mechanism designer.


## Atlas Based Methods
* ### [Synthesis of the whole family of planar 1-DOF kinematic chains and creation of their atlas database :](https://www.sciencedirect.com/science/article/pii/S0094114X11001728)
  - A general method to synthesize planar 1-DOF kinematic chains is proposed.
  - The method is characterized by effectiveness, automation and designer-friendliness.
  - The whole family of 1-DOF kinematic chains with 6–14 links is synthesized.
  - An atlas database of 1-DOF kinematic chains with 6–14 links is established.
  - The atlas database contains all the valid topological graphs classified by their structural characteristics.
    Once topology is selected, the dimensions are calculated by some other
    methods.

* ### [A New Approach to Dimension Synthesis of Spatial Four-Bar Linkage Through Numerical Atlas Method](http://mechanismsrobotics.asmedigitalcollection.asme.org/article.aspx?articleid=1451372)
    (HCPDT: harmonic characteristic parameters of the dimensional type,
    CRAO : coupler rotation-angle operator,
    MBDT: mechanism’s basic dimensional types)
  - Constitute two atlas of RSSR mechanism for function and path generation
    respectively.
    1. Steps of Function Generator
      i. Constitute a numerical atlas database about the output function
          by putting the HCPDT of the output function and the
          MBDT together.

      ii. Obtain the corresponding harmonic component of the prescribed
          output function by utilizing a one-dimensional FFT.
      iii. Carry out identification between the harmonic characteristic
           component obtained from step 2 and the corresponding
           HCPDT in the numerical atlas. Obtain the MBDT of the
           RSSR mechanism by using fuzzy identification method.
      iv. optimize each of the synthesis of the MBDT of RSSR mechanism link dimensional
          types of mechanism S0, h1, h2, h3, S3, and h0.

    2. Steps of Path Generator
      i. Constitute a numerical atlas database by putting the harmonic
          characteristic component’s database of the CRAO and
          the MBDT together.
      ii. Obtain the harmonic component of the prescribed coupler
          curve by utilizing one- and two-dimensional FFTs.
      iii. Based on the results of step 2, obtain the harmonic characteristic
          component of the prescribed coupler curve by utilizing
          normalization processing
      iv. Carry out identification between the harmonic characteristic
          component got from step 3 and the corresponding component
          in the numerical atlas. Decide the MBDT of the RRSS
          mechanism by using fuzzy identification method and calculate
          the CRAO of the MBDT.
      v.  Obtain the harmonic component of the CRAO by utilizing
          one- and two-dimensional FFTs.
      vi. Compute the position for coupler point, true size, and installing
          dimensions of the RRSS mechanism.

* ### [Quick search and selection of curve generating mechanisms from a data collection](https://www.sciencedirect.com/science/article/pii/0094114X94900329)
   Using an harmonic analysis, the coupler curve of any mechanism may be stored as a series of coefficients independent of a mechanism type. A process of normalization can be applied to the coefficients. By storing the normalized coefficients and associated dimensions of a large number of dimensional variants for a particular type of machinery. Catalogs for a wide variety of different types are combined in a library. A method in this library can be created and searched for the best "seed" mechanisms for subsequent optimization.

* ### [Constraint-Based Design & Optimisation Group (CBDO), Mechanical Engineering, University of Bath](http://www.bath.ac.uk/mech-eng/constraintmodelling/Mechanisms.html)
The general procedure for mechanism selection is to specify the required output path and then use the __catalogues__ to find a suitable candidate mechanism. Additional constraints can then be imposed and constraint modelling software used to adapt the selected mechanism to meet these.

    For an [example](http://www.bath.ac.uk/mech-eng/constraintmodelling/Optimization_App.html), a transfer process requires the creation of an approximately triangular path. The initial four bar linkage mechanism comes from the catalogue (and is chosen to avoid obstacles known to be in the area). Additional constraints are imposed at the pick-up and set-down points to specify the required speeds. The resolution process changes all the link lengths and pivot positions and arrives at a design where the speeds are achieved exactly.

    [Here](https://www.cambridge.org/core/services/aop-cambridge-core/content/view/25995608002A0EF1A7D4B871F15EF82B/S0890060406060239a.pdf/representation_and_handling_of_constraints_for_the_design_analysis_and_optimization_of_high_speed_machinery.pdf) is their paper on The representation and handling of constraints for the design, analysis, and optimization of high speed machinery.

## Artificial Intelligence in Kinematic Synthesis

* ### [Knowledge-based approaches for the creative synthesis of mechanisms](https://www.sciencedirect.com/science/article/pii/001044859090030G):

* ### [Design optimization of a spatial six degree-of-freedom parallel manipulator based on artificial intelligence approaches](https://www.sciencedirect.com/science/article/pii/S073658450900060X):
    The neural network-based standard backpropagation learning algorithm and the __Levenberg–Marquardt algorithm__ are utilized to approximate the analytical solutions of system stiffness and dexterity.
    Subsequently, genetic algorithms are derived from the objective functions described by the trained neural networks, which model various performance solutions.

    Neural networks possess the capability of complex function approximation and generalization by simulating
    the basic functionality of the human nervous system in an
    attempt to capture some of its computational strengths. Since the
    objective function must be solved before using genetic algorithms,
    __neural networks will be utilized to represent expressions of the
    solutions for the two performance indices__ of a six-DOF parallel
    manipulator. For the MOO problem, an algorithm that exhibits
    compromise should be executed, since it is impossible to
    maximize or minimize all of the objective function values if they
    conflict with one another. This methodology will not only provide
    effective guidance but will also present a new approach for the
    dimensional synthesis of optimal design in general parallel
    mechanisms.

* ### [An Automated Procedure for Intelligent Mechanism Selection and Dimensional Synthesis](http://mechanicaldesign.asmedigitalcollection.asme.org/article.aspx?articleid=1453070)
    Using an interactive dialogue with a designer; the system converges to an appropriate mechanism configuration satisfying a prescribed synthesis requirements including type of synthesis problems, number of precision positions, and number of independent inputs.

    The user has an option to inquire the selection system to give reasons for the mechanism configuration selection. The automated synthesis procedure uses the data supplied by the selection system to generate the design equations. A powerful numerical algorithm solves the design equations giving all possible solutions without the need of supplying initial guesses. The complete system provides a valuable tool that performs a comprehensive design procedure with minimal user interaction and background knowledge in mechanism design.


Even in Computer-vision course __levenberg-Marquardt algorithm__ was
utilized along with neural net to approximate probability distribution of
variational autoencoders.

## Variational Geometry Approach to Synthesis
- ### [A Variational Approach for the Design of Spatial Four-Bar Mechanism](http://www.tandfonline.com/doi/abs/10.1080/08905459708905279)


### Clustering Using Auto-Encoders:
  [Auto-encoder Based Data Clustering](http://www.nlpr.ia.ac.cn/english/irds/People/lwang/M-MCG_EN/research/CFS-CIAPR13/paper.pdf)
  [Unsupervised Deep Embedding for Clustering Analysis](http://proceedings.mlr.press/v48/xieb16.pdf)

### Sensitivity Analysis
[Sensitivity analysis: strategies, methods, concepts, examples](http://dpannell.fnas.uwa.edu.au/dpap971f.htm)

## Knowledge-based-Planning
Read about KR: [Knowledge representation and reasoning](https://en.wikipedia.org/wiki/Knowledge_representation_and_reasoning)
### [A Knowledge-Based Approach to Planning with Incomplete Information and
Sensing∗](https://www.cs.nmsu.edu/~tson/classes/spring04-579/petricbacchus.pdf)
### [KABouM: Knowledge-Level Action and
Bounding Geometry Motion Planner](http://www.jair.org/media/5560/live-5560-10469-jair.pdf)
