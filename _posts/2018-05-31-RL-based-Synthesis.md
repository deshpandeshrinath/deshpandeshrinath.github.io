---
layout: post
title: "Reinforcement Learning approach to Mechanism Synthesis"
date: 2018-05-31
mathjax: true
---

## Mechanism Synthesis as Constrained Optimization Problem

Mechanism synthesis problems are widely formulated as constrained optimization
problems, where objective function is highly non-linear with non-linear inequality constraints.
Objective function is not necessarily differentiable, which allows only few
optimization techniques applicable for solving like Powell's Local Search,
Differential Evolution (Genetic Algorithms), Simulated Annealing, Particle Swarm
Optimization.

However, Above-mentioned methods do not make use of the rich feedback obtained during
function evaluation.

'Approximate dynamic programming (ADP) has emerged as a powerful tool for tackling
a diverse collection of stochastic optimization problems. Reflecting the wide
diversity of problems, ADP (including research under names such as reinforcement
learning, adaptive dynamic programming and neuro-dynamic programming) has become
an umbrella for a wide range of algorithmic strategies. Most of these involve
learning functions of some form using Monte Carlo sampling.'[(Powell 2012)](http://castlelab.princeton.edu/html/Papers/Powell-Ryzhov-ADP_and_Optimal_LearningFeb2012.pdf)

## Reinforcement Learning
Reinforcement learning (RL) is an area of machine learning, concerned with how
software agents ought to take actions in an environment so as to maximize some
notion of cumulative reward. In RL, the environment is typically formulated as a
Markov decision process (MDP), as many reinforcement learning algorithms for
this context utilize dynamic programming techniques. The focus is about finding
the balance between Exploration and Exploitation

There are following elements in Reinforcement Learning

__The state variable \\(s_t\\):__
The state variable captures the information available at
time t.

__Actions \\(a_t\\):__
Actions, decisions need to be taken by the agent.

__Reward \\(r_t\\):__
The immediate incentive provided for the current state-action pair.
Objective Function is implicitly provided in terms of rewards.

__Policy:__
It is the way we decide which actions to take, based on the current state and goal.
Primary objective of the learning is to learn the policy that maps the states to
action.
There are a few classes of policies, which can be combined depending upon task. e.g. Monte-Carlo Tree Search, Policy Approximation, Value Approximation.

## Use of Domain knowledge:
Design of reward functions and state representation is critical for the success
of Reinforcement Learning.
State representation should be sufficient for the policy to determine which
actions to take, for reaching the goal.


### Possible choices for state representation:

1. Coupler curve
2. Fourbar linkage parameters in terms of link ratios
3. Signatures
4. Fourbar joint coordinates, link ratios, link angles
5. Loci of joint coordinates for entire simulation of coupler curve, along with
   coupler curve
6. Pixels crossed by entire mechanism during motion

### Some questions
- Should we consider all the coupler curves? or just the one corresponding to current
  crank orientation?
- We need geometrical information in order to avoid obstacles, so will going
  invariant to scale and orientation for coupler matching help or hinder?
- can we use Recurrent Neural Network to better represent the state?

### Actions:
1. Percentage Change each linkage length except ground link = 5
2. Percentage Change ground link length and orientation = 3
3. Change branch

### Shaped Reward:
- signature matching (Ignoring obstacle detection)
- Including obstacle detection (signature matching + obstacle avoiding)
- Precision point
    - check the mean squared distance from the closest coupler point to the closest precision point
    - dual-quaternion or some other metric.

### Goal:
- If signature match is within tolerance.
- Constraints are satisfied

### Environment with Sparse Binary Rewards
- rewards are binary, until the goal is reached reward is -1 and after reaching
  goal reward is 0.
- Hindsight Experience Reply approach may prove effective.


## Idea of self play
Two competing agents to win the game, where winner is the one, which satisfies
the synthesis problem in closest manner.

# Work Plan

- Design
  - State Representation
  - Reward Function
  - Policy Structure
- Engineer the overall algorithm that works along with database for computing feasible solutions.

## Current Implementation
- __State__
  - Locus of each joint coordinates during the simulation + link ratios + goal coupler trajectory
- __Reward__
  - The normalized cross-correlation score between target and current coupler trajectory
- __Policy__
  - Actor-Critic Method with episilon-Greedy Policy



# References
- [Temporal Difference Models]( http://bair.berkeley.edu/blog/2018/04/26/tdm/ )

- [Hindsight Experience Replay] (https://arxiv.org/abs/1707.01495)

- [OPTIMAL LEARNING AND APPROXIMATE DYNAMIC PROGRAMMING](http://castlelab.princeton.edu/html/Papers/Powell-Ryzhov-ADP_and_Optimal_LearningFeb2012.pdf)

- [Deep Learning for Real-Time Atari Game Play
Using Offline Monte-Carlo Tree Search Planning](https://web.eecs.umich.edu/~baveja/Papers/UCTtoCNNsAtariGames-FinalVersion.pdf)
    The combination of modern Reinforcement Learning and Deep Learning approaches
    holds the promise of making significant progress on challenging applications
    requiring both rich perception and policy-selection. The Arcade Learning
    Environment (ALE) provides a set of Atari games that represent a useful benchmark
    set of such applications. A recent breakthrough in combining model-free
    reinforcement learning with deep learning, called DQN, achieves the best realtime
    agents thus far. Planning-based approaches achieve far higher scores than the
    best model-free approaches, but they exploit information that is not available to
    human players, and they are orders of magnitude slower than needed for real-time
    play. Our main goal in this work is to build a better real-time Atari game playing
    agent than DQN. The central idea is to use the slow planning-based agents to provide
    training data for a deep-learning architecture capable of real-time play. We
    proposed new agents based on this idea and show that they outperform DQN

- [LEARNING TO ACT BY PREDICTING THE FUTURE](http://vladlen.info/papers/learning-to-act.pdf)
    We present an approach to sensorimotor control in immersive environments. Our
    approach utilizes a high-dimensional sensory stream and a lower-dimensional
    measurement stream. The cotemporal structure of these streams provides a rich
    supervisory signal, which enables training a sensorimotor control model by interacting
    with the environment. The model is trained using supervised learning
    techniques, but without extraneous supervision. It learns to act based on raw sensory
    input from a complex three-dimensional environment. The presented formulation
    enables learning without a fixed goal at training time, and pursuing dynamically
    changing goals at test time. We conduct extensive experiments in threedimensional
    simulations based on the classical first-person game Doom. The
    results demonstrate that the presented approach outperforms sophisticated prior
    formulations, particularly on challenging tasks. The results also show that trained
    models successfully generalize across environments and goals. A model trained
    using the presented approach won the Full Deathmatch track of the Visual Doom
    AI Competition, which was held in previously unseen environments.

- [Reinforcement Learning in Robotics:
A Survey](http://www.ias.tu-darmstadt.de/uploads/Publications/Kober_IJRR_2013.pdf)
    Reinforcement learning offers to robotics a framework
    and set of tools for the design of sophisticated
    and hard-to-engineer behaviors. Conversely, the challenges
    of robotic problems provide both inspiration,
    impact, and validation for developments in reinforcement
    learning. The relationship between disciplines
    has sufficient promise to be likened to that between
    physics and mathematics. In this article, we attempt
    to strengthen the links between the two research communities
    by providing a survey of work in reinforcement
    learning for behavior generation in robots. We
    highlight both key challenges in robot reinforcement
    learning as well as notable successes. We discuss how
    contributions tamed the complexity of the domain and
    study the role of algorithms, representations, and prior
    knowledge in achieving these successes. As a result, a
    particular focus of our paper lies on the choice between
    model-based and model-free as well as between value
    function-based and policy search methods. By analyzing
    a simple problem in some detail we demonstrate
    how reinforcement learning approaches may be profitably
    applied, and we note throughout open questions
    and the tremendous potential for future research.

- [Monte Carlo Tree Search in Continuous Action Spaces with Execution Uncertainty](https://www.ijcai.org/Proceedings/16/Papers/104.pdf)
    Real world applications of artificial intelligence often
    require agents to sequentially choose actions
    from continuous action spaces with execution uncertainty.
    When good actions are sparse, domain
    knowledge is often used to identify a discrete set
    of promising actions. These actions and their uncertain
    effects are typically evaluated using a recursive
    search procedure. The reduction of the
    problem to a discrete search problem causes severe
    limitations, notably, not exploiting all of the sampled
    outcomes when evaluating actions, and not using
    outcomes to help find new actions outside the
    original set. We propose a new Monte Carlo tree
    search (MCTS) algorithm specifically designed for
    exploiting an execution model in this setting. Using
    kernel regression, it generalizes the information
    about action quality between actions and to unexplored
    parts of the action space. In a high fidelity
    simulator of the Olympic sport of curling, we show
    that this approach significantly outperforms existing
    MCTS methods.

- [Combining Neural Networks and Tree Search for Task and Motion
Planning in Challenging Environments](https://arxiv.org/pdf/1703.07887.pdf)
    We consider task and motion planning in complex
    dynamic environments for problems expressed in terms of a
    set of Linear Temporal Logic (LTL) constraints, and a reward
    function. We propose a methodology based on reinforcement
    learning that employs deep neural networks to learn low-level
    control policies as well as task-level option policies. A major
    challenge in this setting, both for neural network approaches
    and classical planning, is the need to explore future worlds of a
    complex and interactive environment. To this end, we integrate
    Monte Carlo Tree Search with hierarchical neural net control
    policies trained on expressive LTL specifications. This paper
    investigates the ability of neural networks to learn both LTL
    constraints and control policies in order to generate task plans
    in complex environments. We demonstrate our approach in a
    simulated autonomous driving setting, where a vehicle must
    drive down a road in traffic, avoid collisions, and navigate an
    intersection, all while obeying given rules of the road.

- [Database Learning](https://arxiv.org/pdf/1703.05468.pdf)

- [Reinforcement Learning as Classification: Leveraging Modern Classifiers](https://users.cs.duke.edu/~parr/icml03.pdf)

- [Continuous Upper Confidence Trees](https://hal.archives-ouvertes.fr/hal-00542673v1/document)
    Upper Confidence Trees are a very efficient tool for solving
    Markov Decision Processes; originating in difficult games like the
    game of Go, it is in particular surprisingly efficient in high dimensional
    problems. It is known that it can be adapted to continuous domains
    in some cases (in particular continuous action spaces). We here present
    an extension of Upper Confidence Trees to continuous stochastic problems.
    We (i) show a deceptive problem on which the classical Upper
    Confidence Tree approach does not work, even with arbitrarily large
    computational power and with progressive widening (ii) propose an improvement,
    termed double-progressive widening, which takes care of the
    compromise between variance (we want infinitely many simulations for
    each action/state) and bias (we want sufficiently many nodes to avoid a
    bias by the first nodes) and which extends the classical progressive widening
    (iii) discuss its consistency and show experimentally that it performs
    well on the deceptive problem and on experimental benchmarks. We
    guess that the double-progressive widening trick can be used for other
    algorithms as well, as a general tool for ensuring a good bias/variance
    compromise in search algorithms
