---
tags:
  - math-493
lecture: "Lecture 13: Composition Series and the Jordan-Hölder Theorem"
aliases:
  - composition series
---
Relevant Courses: [[Math 493]]

> [!info] **Definition: Composition Series**
> 
> Let $G$ be an arbitrary group. A **composition series** is a [[Normal Series|normal series]] $$ (e) = G_0 \triangleleft G_1 \triangleleft \cdots \triangleleft G_k = G $$ with the added condition that $G_{i + 1} / G_{i}$ is simple.

We can then also show the following:

> [!example] **Lemma**
> 
> All finite groups admit a composition series.

> **Proof**
> 
> Let us prove via induction, on the order of the group $G$.
> 
> _Base Case_: $|G| = 1$. This means that the group $G$ must be trivial, so it has only one normal subgroup (itself, or $e$). Thus, $G_k / G_0 = G_k$, which has order 1 so has no proper normal subgroups so is simple. Thus its composition series is the trivial composition series $$ (e) = G_0 = G. $$
>
> _Inductive Assumption:_ For all groups $K$ such that $|K| < n$, we have that $K$ admits a composition series.
> 
> We can split this up into two cases: $G$ is simple or $G$ is not simple.
> 
> Suppose $G$ is simple. Then, it has no normal subgroups except $(e)$ and itself. The only proper subgroup then is $(e) = G_0$, and—since $G$ is simple—$G / G_0 \simeq G$ must also be simple, giving us that the composition series exists and is simple $$ (e) = G_0 \triangleleft G_1 = G. $$
> Contrarily, suppose that $G$ is not simple. Then, $G$ must have at least one nontrivial proper normal subgroup, which we will denote $N$ (meaning $N \triangleleft G$). Since $N$ is a nontrivial proper subgroup, it has order strictly less than $G$ and thus has a composition series $$ (e) = N_0 \triangleleft \cdots \triangleleft N_k = N. $$
> Additionally, $G / N$ has order strictly less than $G$, so must also have a composition series $$ (e) = N/N = \overline{G}_0 \triangleleft \overline{G}_1 \triangleleft \cdots \triangleleft \overline{G}_l = G/N. $$
> By [[The Third Isomorphism Theorem]], there is a bijection between subgroups of $G$ containing $N$, and subgroups of $G / N$ that would map $G_i \to \overline{G}_i$. Moreover, $$\overline{G}_{i + 1} / \overline{G}_i \simeq G_{i + 1} / G_i$$ More importantly, $\overline{G}_l / \overline{G}_{l - 1}$ is simple, which means that $G_l / G_{l - 1}$ is also simple.
> 
> Therefore, we can see that $$ N \triangleleft G_1 \triangleleft \cdots \triangleleft G_{l - 1} \triangleleft G_l = G. $$ And so, we get the composition series $$ (e) = N_0 \triangleleft \cdots N_k = N \triangleleft G_1 \triangleleft \cdots \triangleleft G_{l - 1} \triangleleft G_l = G. $$
> 
> Thus, we have constructively shown that $G$ must have a composition series.
> 
> This proof is complete by induction.



 

 



One of the most important things about the composition series is its relation shipw ith the [[Jordan-Hölder Theorem]].