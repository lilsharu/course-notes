---
tags:
  - game-theory
---
Relevant Courses: [[Game Theory]]

# Best Response
* If you knew what everyone else was going to do, it would be easy to pick your own [[Strategy|strategy]]
* Let $s_{-i} = \langle s_1, \ldots, s_{i - 1}, s_{i + 1}, \ldots, s_n\rangle$.
	* Now, $s = (s_{-i}, s_{i})$

> [!tldr] Definition: Best Response
>
>$s_i^* \in BR(s_{-i}) \iff \forall s_i \in S_i,\, u_i(s_i^*, s_{-i}) \geq u_i(s_i, s_{-i})$

# Nash Equilibrium

> [!tldr]
>
> Nash Equilibrium is a scenario in game theory in which no player in a non-cooperative game has anything to gain by only changing their strategy.

- **A consistent list of strategies*** 
- Each player maximizes their payoff given the action of others
- Nobody has an incentive to *deviate* from their [[Strategy|strategy]] if an equilibrium profile is played
- Self consistent / stable

> [!tldr] Definition: Nash Equilibrium
> $s = \langle s_1, \ldots, s_n \rangle$ is a *Nash equilibrium* if and only if $\forall i, s_i \in BR(s_{-i})$.

We can restrict the definition of Nash Equilibrium to Pure Strategies as well:

> [!tldr] Definition: Pure Strategy Nash Equilibrium
> $a = \langle a_1, \ldots, a_n \rangle$ is a *Nash equilibrium* if and only if $\forall i, a_i \in BR(a_{-i})$.
> 
> It is just a Nash Equilibrium if everyone used a pure (non-random) strategy.
## Verifying Nash Equilibrium

To verify if "pure strategy" is a Nash Equilibrium, there is a simple check: check that nobody wants to deviate. If nobody wants to deviate (for every player, assuming the other two players decision is a constant, there is no better action to take), then you are in Nash Equilibrium.

## Nash's Famous Theorem

> [!important] Nash's Theorem (Nash, 1950)
> Every finite game has a (Mixed Strategy) Nash Equilibrium.

## Computing Mixed Nash Equilibria

It is hard in general to computer Nash Equilibria, but it's easy when you can guess the [[Strategy|support]] (recall that the support is the set of actions that occur with positive probability) of the Nash Equilibria.

In the case of a 2 player game, assume that player 2 plays the arbitrary strategy $s = \langle p_1, p_2, p_3, \ldots, p_n\rangle$ where $\sum_{i \leq n}p_i = 1$. If player 1 responds with the with a mixed strategy, player 2 must make him indifferent between each of the $n$ actions (otherwise player 1 could adjust their mixed strategy to take advantage of the differences). Then, we want to find the values of $p_i$ such that the utility for player 1 is the same:
$$u_1(a_1 \mid \text{ player 2's strategy is } s) = u_1(a_2 \mid s) = \cdots = u_1(a_n \mid s).$$
Then, we can solve for which values of $p_1, p_2, \ldots, p_n$ satisfy the above equality.

Let's say that we get out "nonsensical" output, like a probability larger than 1 or less than 0. Then, that means with the given support, it is impossible to make the other player indifferent (and thus there is no Nash Equilibrium with the given support).