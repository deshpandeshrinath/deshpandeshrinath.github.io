---
layout: post
title: "Data Driven Synthesis"
date: 2018-01-17
mathjax: true
---

The main goal of this approach is to develop a framework to obtain practically useful linkages for the given task of path or motion generation.

The main idea of the current approach is to create a database of all possible
shapes of coupler trajectories, mapped with their known generator linkage.
This data base is stored in a data structure with efficient insertion and query
properties.
This database should also try to learn form the data for faster results.

Whenever an input motion or path is presented, k nearest neighbors corresponding to that
motion or path should be returned.
Since each data point in the dataset corresponds to defect free linkage, a
multitude of solutions with similar coupler trajectories can be extracted.

Here nearest neighbor is defined as motion or path whose part or whole has a
shape which is closest to query motion or path.

## [Literature Surveys]({{ site.baseurl }}{% post_url 2018-01-30-survey-of-mechanism-design %})

## Approach
- ### Representation of Coupler Trajectories
  - Should be invariant to Scale, Rotation, Translation
    - helps in large reduction in redundant data
  - Insensitive to sampling
    - Only Sensitive to shape regardless of timing information.
  - Low dimensionality
    - For efficient insertion and query
- ### Data Generation
  - Data should be generated from such a distribution of linkage parameters
    which maximizes the variance in trajectory space.
- ### Efficient Query Operation
  - Cascaded Queries using Clustering
  - Data Reduction using Competitive Learning Methods like Growing Neural Gas
- ### Optimization of Results obtained from neighbor queries
  - Objective function can optimize the linkage based on partial curve
    matching
  - Where objective function is the shape similarity (part or whole). -> Just
    like S.Kota's objective function of cumulative deviation.
- ### AI techniques for intelligent synthesis:
  - [Build a knowledge-based System](https://en.wikipedia.org/wiki/Knowledge-based_systems)
  - Interactive and intelligent user feedback through machine learning.

## Invariant Representation : Trajectory Signature of coupler path
1. We first use fit a 3rd order B-Spline curve to coupler path.
2. We apply [Invariant Curve Signature developed by M. Cui et. al](http://peterwonka.net/Publications/pdfs/2009.PRL.Ming.CurveMatching2d.Preprint.pdf)
  to the B-Spline curve.
  a. The method is based on computing the integral of curvatures with respect to
  arc length of a curve. This is a way to parameterize curves that is scale invariant.

Figure shows same trajectory in two different scales
![Spatial Curve with different scales]({{ "/assets/data-driven-synthesis/trajectories.png" | absolute_url }})

| Integral of unsinged Curvature (Ks) | Curvature w.r.t. Ks |
|-------|---------|
| ![Curvature_Integrals]({{ "/assets/data-driven-synthesis/Curvature_Integral.png" | absolute_url }}){:width="100%"} | ![Curvatures w.r.t Integral]({{ "/assets/data-driven-synthesis/Signatures.png" | absolute_url }}){:width="100%"}|

### Dimensionality Reduction and Data pre-processing
3. We perform fourier analysis of the obtained signature from the first two
   steps and store first five harmonics of the curve.
4. We store this data point into k-d Tree data structure for efficient query

## Data Generation
The approach is valid for any planar or spatial linkage.
The task is to produce a dataset such that minimum data points should span the maximum volume in
trajectory space.
However we don't know the mapping between probability distribution of trajectory space and mechanisms parameter space.

In the case of 4R Planar fourbar linkage parameters are \\(l_1, l_2, l_3, l_4, l_5, l_6,\\)
where \\(l_5\\), \\(l_6\\) are base and height of the coupler triangle.

### Path shape Hypothesis
__Shape of the Path__ of a fourbar liinkage has a __maximum variation__ when link
ratios are closer to 1, and it decreases with __skewed ratios__.
Thus, if lets say, each ratio is varied between 0.2 to 5.
Then the sampling distribution should look like Log-Normal Distribution as shown
below.

![Sampling-Distribution]({{ "/assets/data-driven-synthesis/current_pd_of_link_ratio.png" | absolute_url }}){:width="50%"}

### Clustering
1. A graph can be built as database.

There are several algorithms for finding Nearest Neighbor on a Graph.
[Efficient K-Nearest Neighbor Graph Construction for Generic Similarity Measures](http://www.cs.princeton.edu/cass/papers/www11.pdf)



## Example : User Input Trajectory
Following Target path is taken with help of MotionGen GUI:

| MotionGen Input | Input Curve |
|-------|---------|
| ![D-Shaped-Curve]({{ "/assets/data-driven-synthesis/user-input-d-shape.png" | absolute_url }}){:width="100%"} | ![Query-path]({{ "/assets/data-driven-synthesis/query-path.png" | absolute_url }}){:width="100%"} |

|  Five Trajectories with closes shapes | Invariant Signatures |
|-------|---------|
|![knn-trajs]({{ "/assets/data-driven-synthesis/5nearest-paths.png" | absolute_url }}){:width="100%"}| ![signatures]({{ "/assets/data-driven-synthesis/all-signatures.png" | absolute_url }}){:width="100%"}  |

__Closest Mechanism__

![mechanism]({{ "/assets/data-driven-synthesis/mechanism.png" | absolute_url }}){:width="40%"}
