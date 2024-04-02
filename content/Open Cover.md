---
tags:
  - math-297
aliases:
  - open cover
---
Relevant Classes: [[Math 297]]

Suppose $(X, \tau)$ is a [[Topological Space]] and $A \subset X$. An *open cover* for $A$ is a collection of open sets $\{\mathcal O_\lambda \mid \lambda \in A\} \subset \tau$ whose union contains the set $A$; that is
$$A \subseteq \bigcup_{\lambda \in A}\mathcal O_\lambda.$$
(Here, $A$ is an indexing set.)

Given an open cover for $A$, a *finite subcover* is a finite sub-collection of open sets from the original open cover whose union still manages to completely contain $A$. A subset $A$ is said to be *[[Compactness|compact]]* provided that every open cover for $A$ has a finite subcover.