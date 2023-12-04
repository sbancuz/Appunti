---
tags:
  - operations_research
---

This is another method for solving ILP. The concept of these algorithms is quite simple, we systematically enumerate all feasible solutions of the problem, evaluate the objective function and choose the best ones. The set of solution for ILP can be represented with a [[Decision tree]].

Let us consider the optimization problem $P:\max \{ c(x): x \in F \}$, we call $P':\max \{ c'(x): x \in F' \}$ a **relaxation** if 
$$
\begin{align}
  & F \subseteq F' \\
  & x \in F \implies c'(x) \geq c(x)
\end{align}
$$
According to this definition we can easily verify that the value of the relaxation of a maximization problem represents an overestimation of the optimal solution value
$$
\zeta(P) \leq \zeta(P')
$$
Now let $\dot{x} \in F'$ be an optimal solution for the relaxation $P'$ and let  $\dot{x}\in F$ and $c(\dot{x})=c'(\dot{x})$, then $\dot{x}$ is optimal solution even for $P$.

>[!tip]
>In defining a relaxation of a problem we generally take into account the fact that the optimal solution of a relaxation should be simpler to compute than the optimal solution of the original problem

There are various types of relaxation techniques:
- Constraints removal: $\min \{ f(x) : x \in X_{1} \cap X_{2} \} \implies \min \{ f(x) : x \in X_{1} \}$
- Continuous relaxation: $\min \{ f(x): x \in \{ 0, 1 \}^{n} \} \implies \min \{ f(x): x \in [0,1]^{n} \}$
- Surrogate relaxation: linear combination of constraints
- Lagrangean relaxation: Penalize some constraints in the objective function
### Branching rules

Branching rules allows to partition the feasible region into subsets, each defining a subproblem having a reduced size in comparison with the original problem. Formally we have a problem
$$
P: \max \{ cx: x\in F \}
$$
and a branching rule defines partitions of $F$ such that
$$
F = \cup F_{i}
$$
and if possible their intersection is empty. When $k = 2$ we call it a **bipartite branching rule**.

![[bipartite branch.png]]
