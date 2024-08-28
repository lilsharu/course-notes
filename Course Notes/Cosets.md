---
tags:
  - math-493
  - definition
---
Let $H$ be a subgroup of $G$.

## Left Cosets

> [!info] **Definition: Left Cosets**
> 
> Let $a \in G$. The left coset $aH$: $$aH = \Set{ah \mid h \in H}$$

> [!question] Example
> 
> Consider [[The Z/nZ Group|Z/4Z]], $G = \mathbb{Z}/4\mathbb{Z} = \Set{0, 1, 2, 3}$.
> 
> Let the [[Subgroup]] $H \subseteq G = \Set{0, 2}$.

>[!important] Proposition 1
>
>Proposition: Any two left cosets of $H$ in $G$ are either identical or disjoint.
>
>In other words, $a,b \in G, \, aH \cap bH \neq \emptyset \implies aH = bH$.
>
>**Proof:**
>Fix $a, b \in G$. Suppose $aH \cap bH \neq \emptyset$.
>
>There exists an $x \in aH \cap bH$. By definition of $aH$ and $bH$, there exists $h_1 \in H$ and $h_2 \in H$ such that $ah_1 = bh_2 = x$.
>$$
>\begin{align*}
>ah_1 = bh_2 &\implies a = bh_2h_1^{-1}\\
>&\implies a \in bH\\
>&\implies aH \subseteq (bH)H = b(HH) = bH.
>\end{align*}
>$$

> [!note] Note: 
> 
> The order of all left cosets of $H$ are the same.


> [!important] Proposition 2
> Proposition: $G$ is the disjoint union of the left cosets of $H$ in $G$.

## Right Cosets









