---
tags:
  - eecs-281
  - eecs-376
lecture: "Lecture 03: Complexity Analysis, Math Foundations"
---
Relevant Classes: [[EECS 281]], [[EECS 376]]

The Asymptotic Upper Bound for a function in the following regard:
$$f(n) = O(g(n)) \iff \exists c > 0 \land n_0 \geq 0 \text{ s.t. }  \forall n \geq n_0, \quad f(n) \leq c \cdot g(n) $$
A sufficient (but not necessary) condition:

If $$\lim_{n \to \infty} \left(\frac{f(n)}{g(n)}\right)= d < \infty$$, then $f(n)$ is $O(g(n))$.

> Note: Since this is just a sufficient (but not necessary) condition, if the limit is not a non-infinite constant, that does not mean that $f(n) \neq O(g(n))$.

This is similar to and related to: [[Big-Theta]] and [[Big-Omega]]