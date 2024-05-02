---
tags:
  - game-theory
---
Relevant Courses: [[Game Theory]]

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