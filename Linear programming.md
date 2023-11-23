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

