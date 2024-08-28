---
tags:
  - game-theory
---
Relevant Courses: [[Game Theory]]

Often, payoffs between players are not relatively measurable: for example, the payoff for Player A might be in lives taken, while for Player B it could be in money stolen from the bank. There isn't any strict "value" you can put to a life in terms of money stolen from the bank. So these two payoffs are like "currencies" that don't have a conversion rate. With these differences in payoff units, how do we determine what is "universally" best? Well, we can't determine what's universally best, but we can come up with a list of options that could be universally best, depending on how much each player's interests are valued. These outcomes are called **Pareto optimal**. 

## Pareto Domination

Let $o$ and $o'$ be arbitrary outcomes of a game. We say that $o$ **Pareto-dominates** $o'$ if outcomes $o$ is at least as "good" for every agent as $o'$, AND there is at least one agent who strictly prefers $o$ to $o'$.

>[!summary] Summary: Pareto Domination
>
> Let $o$ and $o'$ be arbitrary outcomes of a [[Games (Game Theory)|game]] $G = \langle \mathbb{N}_{\leq n}, A, u\rangle$ with $n$ players. Let's say $o$ and $o'$ are defined by a set of actions $o = (a_1, \ldots, a_n)$ for each player, and $o' = (a'_1, \ldots, a'_n)$.
>
> $o$ is said to **Pareto-dominate** $o'$ if, $\forall i$, $u_i(a_i) \geq u_i(a'_i)$ and $\exists k$ for which $u_k(a_k) > u_k(a'_k)$.

## Pareto Optimal

> [!summary] Definition: Pareto Optimal
> An outcome $o^*$ is **Pareto-optimal** if there is no other outcome that Pareto-dominates it.

Note that every game has at least one Pareto-optimal outcome.