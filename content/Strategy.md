---
tags:
  - game-theory
aliases:
  - strategy
---
There are many ways to approach a game: either deterministically or probabilistically. We can generalize the idea of a strategy using this idea.

> [!summary] Definition: Strategy
> 
> A **strategy** $s_i$ for an agent $i$ is any probability distribution over a set of actions $A$.
> 
> Using this idea, we can classify strategies into a few types
> 
> - a **pure strategy** is a strategy where *only one* action is played with positive probability
> - a **mixed strategy** is one where *more than one* action is played with positive probability. 
> 	 - These actions are called the **support** of the mixed strategy.

> [!example] Example: Mixed Strategy
> 
> Consider the game of Rock Paper Scissors: if you use any deterministic strategy, your opponent—after observing for a sufficient period of time—would know exactly how you would behave and thus always win. Thus, a mixed strategy must be employed

However, now that our strategies are probabilistic in nature, the definition of utility becomes less straightforward. Thus, we can instead use the *expected utility* from decision theory.

> [!summary] Expected Utility
> 
> The expected utility for an agent $i$ for a strategy $s$ is:
> $$u_i = \sum_{a \in A}u_i(a)\Pr(a \mid s)$$
> 
> where $$\Pr(a \mid s) = \prod_{j \in N}s_j(a_j)$$

# Interpreting Mixed Strategy Equilibria

What does it mean to play a mixed strategy?

- Randomize to confuse your opponent
- Randomize when uncertain about the other's actions
- Mixed strategies are a concise description of what might happen in repeated play: count of pure strategies in the limit
- Mixed strategies describe population dynamics: suppose a population has agents with different deterministic strategies, the mixed strategy could describe the distribution of strategies seen in the population (if you randomly selected an agent, what's the probability that they select a certain strategy)