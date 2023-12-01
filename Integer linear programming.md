---
tags:
  - operations_research
---
Let us consider an ILP problem
$$
\begin{align}
\min  &  \text{ } cx  \\
	 & Ax\geq b \\
	 & x\in \mathbb{Z}^{n}_{+}
\end{align}
$$
with its geometric representations represented as

![[ilp.png]]

>[!note]
>The feasible region is not a convex set anymore, as it was the case in [[Linear programming]], consequently the relevant algorithms cannot be directly applied to this class of problems

If we generalize the approach used in [[Disjunctive constraints]] an in the [[Machine task scheduling]] we can consider the problem of determining a solution satisfying at least $k\leq n$ of the constraints.
Let $M\in \mathbb{R}: A_{i}-b_{i}\leq M$ for each feasible $x,i=1,\dots,n$ then the problem can be formulated as
$$
\begin{align}
 & A_{i}x-b_{i}\leq b_{i}My_{i} \\
 & \sum y_{i} \leq n - k \\
	 & y \in \{ 0,1 \}
\end{align}
$$

