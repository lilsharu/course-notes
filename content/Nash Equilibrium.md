---
tags:
  - game-theory
---
Relevant Courses: [[Game Theory]]

## Best Response
* If you knew what everyone else was going to do, it would be easy to pick your own action
* Let $a_{-i} = \langle a_1, \ldots, a_{i - 1}, a_{i + 1}, \ldots, a_n\rangle$.
	* Now, $a = (a_{-i}, a_{i})$

```ad-summary
title: Definition: Best Response

$
a_i^* \in BR(a_{-i}) \iff \forall a_i \in A_i,\, u_i(a_i^*, a_{-i}) \geq u_i(a_i, a_{-i})
$
```

## Nash Equilibrium

```ad-summary
title: Definition: Nash Equilibrium

Nash Equilibrium is a scenario in game theory in which no player in a non-cooperative game has anything to gain by only changing their strategy.
```

* ***A consistent list of actions*** 
* Each player maximizes their payoff given the action of others
* Nobody has an incentive to *deviate* from their action if an equilibrium profile is played
* Self consistent / stable

```ad-summary
$a = \langle a_1, \ldots, a_n \rangle$ is a ("pure strategy") *Nash equilibrium* if and only if $\forall i, a_i \in BR(a_{-i})$.
```