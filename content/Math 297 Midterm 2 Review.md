---
tags:
  - math-297
  - content-summary
---
Relevant Classe: [[Math 297]]

# Content
Worksheets Covered: *Worksheet 01 - Worksheet 23*

Homework Covered: *Homework 01 - Homework 10a*

# Questions and Inspiration
## Worksheet 13 - Topology: Sequential Compactness
### Question 170. 
**Let $S = \{1/n \mid n \in \mathbb{N}\}$.**

**Show that the collection of [[Topological Space|open sets]] $\mathcal{C} = \{B_{1/m(m+1)}(1/m) \mid m \in \mathbb{N}\}$ is an [[Topological Space|open cover]] for $S$**

> Fix any element in $S$; it is in some set in $\mathcal C$, so $\mathcal C$ is an open cover of $S$

**Does $\mathcal C$ contain a finite subcover of $S$**

> Fix an $n \in \mathbb{N}$. Only a single element of $\mathcal C$ contains $1/n$ (specifically, the one centered around $1/n$). Therefore, no finite subcover exists, because $\mathbb N$ is unbounded and has infinitely many elements.

### Question 171
**Show that every finite subset of $\mathbb R$ is [[Compactness|compact]] in $\mathbb R$.**

> Fix a finite subset of $S \subsetneq \mathbb R$. Fix an open cover $C$ for $S$. For each $s \in S$, there is at least one $\mathcal O \in C$ such that $s \in \mathcal O$. Choose one and denote this $O_s$. If we take the subcover $C' \subseteq C$ defined by $C' := \{O_s \mid s \in S\}$, it is finite (since $S$ is finite) and a cover (since each $s \in S$ is covered by at least one ball, namely $O_s$). Therefore, a finite subcover must exist for every open cover $C$. Therefore, $S$ is compact.

### Question 172
**Show that $\mathbb N$ is not compact in $\mathbb R$**

> Consider the open cover $\mathcal C = \{B_1(n) \mid n \in \mathbb N\}$

### Question 173
**Let $A$ be an unbounded subset of an [[Inner Product Space|inner product space]] $V$. By considering the [[Open Cover|open cover]] $C = \{B_\ell(\vec 0) \mid \ell \in \mathbb N\}$, show that $A$ cannot be [[Compactness|compact]]. Conclude that every compact subset of $V$ must be bounded.**

> Fix any finite subset of $C' \subseteq C$. Take the max $\ell$ of all the balls. . Because it's unbounded, there exists an element $a \in A$ that is outside of $B_\ell(\vec 0)$ because $A$ is unbounded. Therefore, $C'$ is not a finite subcover. Therefore, no finite subcover exists.
> 
> **By the contrapositive, if $A$ is compact, it is bounded.**

### Question 174
**Suppose $D$ is a subset of an inner product space $V$ that is not closed. Suppose $\vec v \in \bar D \setminus D$. By considering the [[Open Cover|open cover]] $C = \{V \setminus \bar B_{1/n}(\vec v) \mid n \in \mathbb N\}$ of D, show that $D$ can not be [[Compactness|compact]]. Conclude that every compact subset of $V$ must be closed.**

> Fix $O_n \in C$. Notice that the complement of $O_n$ is closed (the closure of $B_{1/n}(\vec v)$), so $O_n$ is open (and by the [[Archimedean Property]], for all elements in $D$ there is an $O_n$ that contains it).
> 
> Fix any finite subset $C' \subsetneq C$. Choose the $O_n \in C'$ corresponding to the largest $n \in \mathbb N$. Because the natural numbers are unbounded in the real numbers, there exists a real number $r \in \mathbb R$ such that $r < 1/n$. This means that all elements in $D \cap B_r(\vec v)$ are not in any open set $O_n$. Therefore, $C'$ is not a finite subcover. This means that all finite subsets of $C$ are not finite subcovers, so no finite subcovers exists.
> 
> **By the contrapositive, if D is compact, then D is closed.**

### Question 175
**Show that if $K$ is a compact subset of an [[Inner Product Space]], then $K$ is closed and bounded**

> Just use 173 and 174

### Question 176
**Let $A$ be an unbounded subset of an [[Inner Product Space]] $V$. For each $n \in \mathbb N$, choose $\vec{a_n} \in A\setminus B_n(\vec{0})$. Show that $(\vec{a_n})$ does not have a convergent subsequence and so $A$ cannot be [[Sequential Compactness|sequentially compact]]. Conclude that every [[Sequential Compactness|sequentially compact]] subset of $V$ must be bounded.**

> Fix an unbounded subset $A \subseteq V$. Let $E_n = A \setminus B_n(\vec 0)$. $E_n$ is nonempty because it is unbounded: for any $n \in \mathbb N$, there exists an element $\vec a_n \in A$ such that $\lVert \vec a_n \rVert \geq n$, which means that $\vec a_n \notin B_n(\vec 0)$. This means that there exists an $\vec a_n \in E_n$. 
> 
> Let $(\vec a_n)$ be a sequence of elements, where $\vec a_n \in E_n$. Fix any subsequence $(a_{n_k})$ of $(\vec a_n)$. Since $n_k > n$, for each $M$ there exists at least one element (actually, an infinite number of elements) such that $\lVert a_{n_k} \rVert \geq M$ because $n_k \geq M$. Since The subsequence is unbounded, it does not converge. Therefore, no convergent subsequences exist, so $A$ cannot be sequentially compact.
> 
> **By the contrapositive, if a subset $A \subseteq V$ is sequentially compact, it must be bounded.**

**Show that every bounded and closed interval in $\mathbb R$ is [[Sequential Compactness|sequentially compact]].**

> Fix any bounded and closed interval, $I \subseteq \mathbb R$. Fix any sequence $(i_n)$ on $I$. Because it is bounded, by the [[Bolzano-Weierstrass Theorem]], it contains a convergent subsequence $(i_{n_k}) \to i$. Since $I$ is closed, all convergent sequences must converge to an element in $I$, so $i \in I$. Since $(i_n)$ was arbitrary, all sequences in $I$ contain a convergent subsequence that converges to something in $I$. Therefore, $I$ is sequentially compact.

### Question 177
**Recall that in Prompt 164 you showed that a subset of a finite dimensional [[Inner Product Space]] is closed if and only if every [[Cauchy Sequence]] in the subset converges to an element of the subset. Use this result to show that a sequentially compact subset of an [[Inner Product Space]] is closed.**

> Let $(V, \langle , \rangle)$ be an inner product space. Let  $A \subseteq V$ be a sequentially compact subset of $V$.
> 
> Fix a [[Cauchy Sequence]] $(a_n)$ in $A$. Because $A$ is sequentially compact, it contains a convergent subsequence $(a_{n_k}) \to a$, where $a \in A$. Because $(a_n)$ is Cauchy, it also converges; therefore, it must also converge to $a$. So it converges to an element in $A$. Therefore, $A$ is sequentially closed, so $A$ is also closed.

### Question 178: Prove the [[Heine-Borel Theorem]]
**A Subset $C$ of a finite dimensional inner product space $(V, \langle , \rangle)$ is [[Sequential Compactness|sequentially compact]] if and only if it is both closed and bounded**.

> **$\implies$ Suppose $C$ is sequentially compact.**
> By 177, $C$ must be closed. By 176, $C$ must be bounded. Therefore, $C$ is closed and bounded.
> 
> **$\impliedby$ Suppose $C$ is closed and bounded.**
> By 176, $C$ must be sequentially compact.

### Question 179
**Show that every nonempty [[Sequential Compactness|sequentially compact]] subset of $\mathbb R$ has both a [[Maximum|maximum]] and a [[Minimum|minimum]].**

> Fix $C \subsetneq R$ such that $C$ is sequentially compact. Therefore, $C$ is closed an bounded.
> 
> Because $C$ is bounded (and $\mathbb R$ is complete), $\sup C$ and $\inf C$ exist. And because $C$ is closed, if $\sup C$ and $\inf C$ exist, they are both respectively in $C$. Therefore, since $\sup C \in C$, $C$ has a maximum (and conversely, since $\inf C \in C$, $C$ has a minimum).

## Worksheet 14
