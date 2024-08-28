---
tags:
  - eecs-203
  - math-297
---
Relevant Courses: [[EECS 203]], [[Math 297]]

# [[Proof by Contradiction]]

First, recall that a [[Rational Number]] is a number that can be written as the quotient of an [[Integer]] and a non-zero [[Natural Number]]. Furthermore, every rational number has a "simplified" form, where the quotient and divisor have no common factors (and thus are [[Relatively Prime]]). 

Assume for contradiction that $\sqrt2$ is rational. That means that there exists an integer $p \in \mathbb Z$ and nonzero $q \in \mathbb{Z}_{>0}$  such that $\sqrt 2 = \frac{p}{q}$. If we square both sides, we get that $2 = \frac{p^2}{q^2}$, which implies that $2q^2 = p^2$. Therefore, $p^2$ is even. This can only be true if $p$ is even. But this means that $p^2$ is actually divisible by 4, hence $q^2$ must also be even, and so therefore $q$ must be even. So that means both $p$ and $q$ are even, which is a contradiction to our assumption that they have no common factors.

Therefore, our initial assumption must be false, so $\sqrt 2$ is not rational, which means it must be irrational.