---
tags:
  - operations_research
---
Linear programming problems are characterized by a linear objective function in decision variables and by constraints described by linear inequalities or equations. Linear programming problems have also a geometric representation with **half-spaces** and **hyperplanes**

A linear programming problem is an optimization problem defined on $x$ variables taking values in $\mathbb{R}^{n}$ and characterized by the following properties:
- the objective function is linear
- the feasible region is defined by a finite set of linear constraints of the type $h(x)=y$ and/or $h(x)\geq\leq y$

A LP problem can be synthetically expressed by means of the following form
$$
\begin{align}
\max & \text{ } cx \\
	 & Ax\leq b \\
	 & x\geq 0
\end{align}
$$
where $A\in \mathbb{R}^{m\times n}$, $c\in \mathbb{R}^{m}$ and $b\in \mathbb{R}^{n}$. This form of LP problem is called **canonical** or **general**. 
### Geometric representation

When presented with canonical LP problems with 2 or 3 variables, we can make use of a geometric representation in order to get a better intuition for the problem. We model constraints as straight lines that represent the boundaries of the half-spaces defined by the constraints themselves. The non-negativity constraint is represented by the Cartesian axes.

![[geometric.png]]

The constraint linking the 2 points $(2,6),(4,3)$ are called **faces** and the green line represent the gradient of the function.

>[!tip]
>It's provable to say that if the optimal solution exists as finite, then it is a vertex, moreover if a point in a face is an optimal solution, then all the points of the face are optimal as well
### Dual problem

With each LP problem we may associate another problem -- called **dual** -- providing information concerning the solution.

![[dual.png]]

From this example we can clearly see that 2 problems are present
$$
\begin{aligned}
\max & \text{ } cx \\
	 & Ax\leq b \\
	 & x\geq 0
\end{aligned} \iff
\begin{aligned}
\max & \text{ } yb \\
	 & yA\leq c \\
	 & y\geq 0
\end{aligned} 
$$
This relation holds not only for this example, but for every LP problem and are called **symmetric pairs**. The first problem is called the **primal** and the other the **dual**.

>[!note]
>The dual of the dual is the primal

Given a LP problem in any form, we can always derive its dual in an automatic way.
### Weak duality theorem

If $P$ and $D$ admit the feasible solutions $\dot{x}$ and $\dot{y}$, respectively, then $c\dot{x}\leq \dot{y}b$

>[!corollary]
>If $\dot{x}$ and $\dot{y}$ are feasible solutions and $c\dot{x}=\dot{y}b$ then the two solutions are optimal

In case we are provided with a feasible solution for the primal and a feasible solution for the dual we may be sure that none of the two can be improved.

>[!corollary]
>If $P$ has unbounded optimality, then $D$ is empty

In fact, even if $D$ contained only one solution, its value would represent a bound to the value of the solutions of $P$.
### Feasible growth directions

Let $\dot{x} \in \mathbb{R}^{n}$ be a feasible solution for $P$, the question is whether such solution is optimal or it is improvable. We can state that is there exists a point $\dot{x}$ better than $\ddot{x}$, it must be possible to express it in the form
$$
\dot{x} = \ddot{x} + \lambda \xi
$$
where $\lambda>0$ is a scalar called **displacement step**, and $\xi$ is a vector of $\mathbb{R}^{n}$ called **displacement direction**. So we can say that $\ddot{x}$ is improvable iff there exists a **feasible growth direction** $\xi$ for which a point $\dot{x}$ still falls in the interior of the feasible region and has objective function value $c\dot{x}>cx$. In other terms, $\ddot{x}$ is optimal iff there exists no such direction $\xi$.

Formally we can say that optimality conditions for $P$ at point $\ddot{x}$ are the non-existence of a solution for
$$
\begin{align}
c\xi > 0 \\
A_{I}\xi \leq 0
\end{align}
$$
where $A_{I}$ indicates the sub-matrix of $A$ relative to the active constraints $I(\ddot{x})$ 