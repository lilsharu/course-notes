---
tags:
  - math-297
  - definition
aliases:
  - limit
---
Relevant Classe: [[Math 297]]

> [!summary] 
> Suppose $(V, \langle , \rangle_V)$ and $(W, \langle , \rangle_W)$ are finite dimensional [[Inner Product Space|inner product spaces]]. Suppose $A \subseteq V$, $\vec v$ is a limit point of $A$, $\vec w \in W$, and $f: A \to W$ is a function. We say $\lim_{\vec x \to \vec v}f(\vec x) = \vec w$ provided that for all $\varepsilon > 0$ there is a $\delta > 0$ such that 
$$\text{whenever } \vec x \in A \text{ and } 0 < \lVert \vec x - \vec v \rVert_V < \delta, \text{ it follows that } \lVert f(\vec(x) - \vec w) \rVert < \varepsilon$$