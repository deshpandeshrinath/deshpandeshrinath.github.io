---
layout: post
title: "Intelligent Machine Design for Motion Generation"
date: 2018-03-20
mathjax: true
---

# Mechanism Synthesis

1. Created a database of mechanical linkages.
2. We do clustering, and neighbor search.
3. We can perform optimization.

## Aim: To create a assistance system that can help designers to get good-practical mechanisms.

## Problems with current approach:
- We don't have clustering based on correlation metric.
- Sorting is only based on similarity score, and we get so many similar
  solutions. It is hard to manually sort good solutions. Sorting should consider
  other practical aspects such as dynamics, pivot locations, etc.
- We don't have any learning or user feedback to learn the goodness of
  mechanism returned.
- No Designer-Framework dialogue.

## What AI can do:
- Reinforcement Learning instead of optimization towards synthesis.
- Creating a knowledge base system, that can guide user towards mechanism
  design.
- Classification of mechanisms based on their properties or something.
- Learning a function that determines goodness/ suitability of a mechanism
  with respect to the task based on user feedback. (This can be used to sort
  the search results.)
- Agent that can intelligently interact with user in a design process.

## Reinforcement Learning
Usually RL involves changing the agents behavior so it’s more likely to take actions that resulted in high rewards in the past - this is the “learning” part.
In contrast to Optimization, where we don't learn from out __past experiences__.
- Agent can learn from past to avoid infringing constraints that are hard to
  mathematically specify in optimization routines.
  - For ex. Obstacle avoidance, dynamic constrains, some common sense aspect of
    the design which a designer would consider but optimization can't.

# References

1. [Reinforcement Learning or Evolutionary Strategies? Nature has a solution: Both](https://medium.com/beyond-intelligence/reinforcement-learning-or-evolutionary-strategies-nature-has-a-solution-both-8bc80db539b3)
