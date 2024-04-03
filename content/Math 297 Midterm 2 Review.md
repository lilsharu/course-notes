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

### Question 182

**Suppose $(V, \langle, \rangle)$ is a finite dimensional [[Inner Product Space]]. Let $A$ and $B$ be nonempty subsets of $V$ such that $V = A \cup B$. We will construct [[Cauchy Sequence|Cauchy Sequences]] $(\vec a_n)$ in $A$ and $\vec b_n$ in $B$ that both converge to the same element of $V$.**

**Since $A$ and $B$ are nonempty, we can choose $\vec a_1 \in A$ and $\vec b_1 \in B$. Let $\vec c_1 = (\vec a_1 + \vec b_1) / 2 \in V$. Since $\vec c_1 \in V = A \cup B$, we know that that $\vec c_1 \in A$ or $\vec c_1 \in B$. If $\vec c_1$ belongs to $A$, then define $\vec a_2 = \vec c_1$ and $\vec b_2 = \vec b_1$. Otherwise,  set  $\vec a_2 = \vec a_1$ and $\vec b_2 = \vec c_1$. How would we define $\vec c_2$? $\vec a_3$?...**

> Repeat the same process, but generalize for an arbitrary $\vec a_i$ and $\vec b_i$.

**Show that both $(\vec a_n)$ and $(\vec b_n)$ are Cauchy.**

> You can prove this more rigorously, but essentially the gap between $a_i$ and $a_{i + 1}$ is at least one half of the distance between $a_i$ and $b_i$. This means that, inductively, the distance is less than $1/2^i \cdot |b_1 - a_1|$. Since the distance between consecutive elements is decreasing geometrically, we have already proved that it must be Cauchy (using the [[Geometric Series|geometric series]] formula)

**Show that there is a vector $\vec v \in V$ such that $\vec a_n \to \vec v$ and $\vec b_n \to \vec v$.**

> Because $(a_n)$ and $(b_n)$ are Cauchy, they are convergent. Denote $\lim a_n = v$ and $\lim b_n = \ell$.
> 
> Consider the sequence $(d_n) = (b_n - a_n)$. Fix any $\varepsilon > 0$. There exists an $N \in \mathbb N$ such that $\forall n \in \mathbb N_{>N}$, $b_n - a_n = |b_1 - a_1| \cdot \frac{1}{2^{n - 1}} < \varepsilon$. Therefore, $d_n \to 0$.
> 
> Both $(a_n)$ and $(b_n)$ are monotonic and bounded between by $a_1, v$ and $b_1, \ell$ respectively. Since the sequences get arbitrarily close to each other and they converge, their limits must be the same.

**Conclude that every finite dimensional [[Inner Product Space]] is connected.**

> By the above construction, we can see that either $\bar A \cap B$ is nonempty (a sequence in $A$ converges to something in $B$) or $\bar B \cap A$ is nonempty by the same reasoning.

### Question 183
**The above problem suggests a general approach for determining if a subset of a finite dimensional [[Inner Product Space]] is connected. Suppose $(V, \langle, \rangle)$ is a finite dimensional inner product space. Show that a subset $E$ of $V$ is connected if and only if for all nonempty disjoint subsets $A, B \subseteq V$ for which $E = A \cup B$ there exists a [[Cauchy Sequence|Cauchy sequence]] contained in one of $A$ or $B$ that converges to an element of the other.**

> $\implies$ Suppose $E$ is connected.
> 
> Fix any disjoint subsets $A \cup B$ such that $E = A \cup B$. Without a loss of generality $\bar A \cap B \neq \emptyset$. Fix $\ell \in \bar A \cap B$ because it is nonempty. Since $\ell \in \bar A$, there exists a Cauchy sequence in $A$ that converges to $\ell$. $\ell \in B$ as well, so this sequence converges to an element of $B$.
> 
> $\impliedby$ Suppose for all nonempty disjoint subsets $A, B \subseteq V$ for which $E = A \cup B$ there exists a Cauchy sequence contained in one of $A$ or $B$ that converges to an element of the other. 
> 
> Fix $A, B$ such that $A \sqcup B = E$. Without a loss of generality, say there exists $(a_n)$ in $A$ that converges to an $\ell \in B$. That means that $\ell \in \bar A$ because the [[Closure]] is equal to the [[Sequential Closure]] in finite dimensional inner product spaces. $\ell \in \bar A \land \ell \in B \implies \ell \in \bar A \cap B$.
> 
> This means that $E$ is not disconnected, and therefore must be connected.

### Question 185, 186, 187

**Show that for every subset $D$ of $\mathbb R$, $D$ is connected if and only if $D$ is an interval.**

> **$\implies$ Let us prove the contrapositive: Suppose $D$ is not an interval.**
> 
> There exists $x, y, z \in R$ such that $x < y < z$; $x, z \in D$; and $y \notin D$.
> 
> Let $X = D \cap (-\infty, y)$ and let $Y = D \cap (y, \infty)$. Because $y \notin D$, we can easily see that $X \sqcup Y = D$.
> 
> $\bar X = \overline{D \cap (-\infty, y)} \subseteq \overline{D} \cap \overline{(-\infty, y)} = \bar D \cap [-\infty, y]$. $\bar X \cap Y \subseteq D \cap \bar D \cap [-\infty, y] \cap (y, infty) = \emptyset$, so $\bar X \cap Y = \emptyset$. 
> 
> Following similar logic, the opposite is also true. Therefore, $D$ is not connected.
> 
> $\impliedby$ **Let us prove via contradiction: Suppose $D$ is an interval. Assume for contradiction that $D$ is not connected.**
> 
> There exists two nonempty disjoint sets $X, Y \subseteq V$ such that $X \sqcup Y = D$ and $\bar X \cap Y = \emptyset = X \cap \bar Y$. Fix $x \in X$ and $y \in Y$. Without a loss of generality, $x < y$.
> 
> Consider the set $G = \{a \in X \mid a \leq y\}$. Let $\alpha = \sup G$. We can see that $x \leq \alpha \leq y$. Because $D$ is an interval, $\alpha \in G$, and thus $\alpha \in \bar X$. Now, because $\bar X \cap Y = \emptyset$, $\alpha < y$. 
> 
> Now consider the set $Z = \{b \in Y \mid b \geq \alpha\}$, and let $\beta = \inf Z$. Similarly, we can see that $\alpha \leq \beta \leq y$. 
> 
> $\lambda \leq b$ because otherwise, $b \in X$ which is a contradiction because $X$ and $Y$ are disjoint.
