---
tags:
  - game-theory
---
Relevant Courses: [[Game Theory]]

## Domination

Let $s_i$ and $s'_i$ be two [[Strategy|strategies]] for player $i$, and let $S_{-i}$ be the set of all possible strategy profiles for the other players.

> [!summary] Definition: Strict Domination
> 
> $s_i$ **strictly dominations** $s'_i$ if $\forall s_{-i} \in S_{-i}$, $u_i(s_i, s_{-i}) > u_i(s'_i, s_{-i})$. In other words, for all situations (no matter what the other players do), person $i$ is strictly better off using strategy $s_i$ over strategy $s'_i$ (without fail).

> [!summary] Definition: Very Weak Domination
>
> $s_i$ **very weakly dominates** $s'_i$ if $\forall s_{-i} \in S_{-i}$, $u_i(s_i, s_{-i}) \geq u_i(s'_i, s_{-i})$. In other words, for all situations (no matter what the other players do), person $i$ is better off or the same using strategy $s_i$ over strategy $s'_i$.


### Equilibria and Dominance

* If one strategy dominates all other strategies, we say it is **dominant**.
* A strategy profile consisting of dominant strategies for every player must be Nash equilibrium
	* An equilibrium in *strictly dominant* strategies must be unique.