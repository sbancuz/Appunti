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

In case the values of $x\in\mathbb{Z}^{n}$ then we are resolving an [[Integer linear programming]] problem.
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
\min & \text{ } yb \\
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

Let $\dot{x} \in \mathbb{R}^{n}$ be a feasible solution for $P$, the question is whether such solution is optimal or it is improvable. We can state that there exists a point $\ddot{x}$ better than $\dot{x}$, it must be possible to express it in the form
$$
\ddot{x} = \dot{x} + \lambda \xi
$$
where $\lambda>0$ is a scalar called **displacement step**, and $\xi$ is a vector of $\mathbb{R}^{n}$ called **displacement direction**. So we can say that $\ddot{x}$ is improvable iff there exists a **feasible growth direction** $\xi$ for which a point $\dot{x}$ still falls in the interior of the feasible region and has objective function value $c\dot{x}>cx$. In other terms, $\ddot{x}$ is optimal iff there exists no such direction $\xi$.

Formally we can say that optimality conditions for $P$ at point $\ddot{x}$ are the non-existence of a solution for
$$
\begin{align}
c\xi > 0 \\
A_{I}\xi \leq 0
\end{align}
$$
where $A_{I}$ indicates the sub-matrix of $A$ relative to the active constraints $I(\ddot{x})$. Also, when moving along $\xi$ we must take care not to go out of the feasible region. The choice of the displacement step is made such that 
$$
\lambda\leq b_{i}-\frac{A_{i}\ddot{x}}{A_{i}\xi} \text{   } \forall {i} \in {I(\ddot{x})} 
$$
We can express these constraints as a LP problem where
$$
\dot{P} : \text{ } \begin{aligned}
\max \text{ }&c\xi \\
  & A_{I}\xi\leq 0
\end{aligned}
\text{ } \dot{D} : \text{ } \begin{aligned}
\min \text{ }&0\eta \\
  & \eta A_{I} =  c\\
  & \eta \geq 0
\end{aligned}
$$
>[!note]
>$\dot{D}$ is useless because any feasible solution has value $0$, this means that is only a feasibility problem
#### Theorem

Consider a problem $P$, a feasible solution $\dot{x}$ of $P$ and the problems related to the search for feasible growth directions $P'$ and $D'$. If $D'$ has a solution, then $\dot{x}$ is an optimal solution for $P$.

```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{SimplexPrimaDual}{$A,b,c,x,unbounded, y$}
	\State optimal $\gets$ \false; unbounded $\gets$ \false
	\State $I \gets \{ i: A_i x = b_i\}$
	\If{$I = \emptyset$}
		\State growAlong($c,x,I,unbounded$)
	\EndIf
	\While{optimal \and unbounded}
		\If{$\{\eta A_I = c\}$ has no solution}
			\State $\xi \gets$  computeXi($\{A_I \xi = 0, c \xi = 1\}$)
			\State growAlong($\xi, x, I, unbounded$)
		\Elif{$\{\eta A_I = c\}$ has solution $\land \exists h: \eta h <0$}
			\State $\xi \gets$  computeXi($\{A_I \xi = u_h\}$)
			\State growAlong($\xi, x, I, unbounded$)
		\Else 
			\State optimal $\gets $ \true
		\EndIf
	\EndWhile
\EndProcedure
\end{algorithmic}\end{algorithm}
```
In the first phase of the procedure the given point $x$ is in the strict interior of all constraints, so we are free to choose any growth direction. The procedure now chooses $\xi=c$, which is the direction providing the greatest increment.
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{growAlong}{$\xi,x,I,unbounded$}
	\State $\lambda = \min \{ \frac{b_i - A_ix}{A_i \xi}, \infty \}$
	\If{$\lambda = \infty$}
		\State unbounded = \True
	\Else
		\State $x \gets x + \lambda \xi$
		\State $I = \{i: A_ix=b_i\}$
	\EndIf
\EndProcedure
\end{algorithmic}\end{algorithm}
```
This procedure computes the displacement step along the direction $\xi$ that was taken as input and returns the new solution $x$ and the new set of active constraints.
### Strong duality theorem

If $P$ and $D$ admit feasible solutions, the $\max \{ cx: Ax\leq b \} = \,min \{ yb: yA=c,y\geq 0 \}$

An immediate consequence of the strong duality theorem is a method for detecting if we are in front of an optimal solution. In fact, $\dot{x}$ is optimal for $P$ iff $c$ belongs to the cone generated by active constraint gradients/
### Optimum theorem

If $P$ has finite optimum, then $D$ also has finite optimum.

![[lp optimum.png]]

### Determination of a feasible solution

Let us consider the problem
$$
P: \begin{align}
\max  & \text{ }cx \\
	 & Ax\leq b
\end{align}
$$
If $b\geq 0$, then $\dot{x} = 0$ is banally a feasible solution for $P$. In case there exists some negative known terms, we need to solve an auxiliary problem in order to achieve a feasible starting solution. Let $J_{+} \{ i:b_{i\geq 0} \}$ and $J_{-}\{ i: b_{i}<0 \}$ and build the auxiliary problem as such
$$
AP : \begin{align}
 & \text{ } \max -ev \\
	 & A_{J_{+}}x \leq b_{J_{+}} \\
	 & A_{J_{-}}x = v\leq b_{J_{-}} \\
	 & -v \leq 0
\end{align}
$$
and it can be immediately verified that $x = 0, v=-b_{J_{-}}$ is a feasible solution for $AP$. The simplex primal dual allows to determine an optimal solution $(\dot{x},\dot{v})$ of $AP$. Observe that an optimal solution exists and is found just by running the simple primal dual algorithm twice.

![[Complementary slackness theorem]]
### Sensitivity analysis

In order to build LP models, approximations may have been made, and if that is the case non-linear phenomena have been considered as linear. Therefore, it's useful to know how stable the detected solution is, or, in other words, how sensible it is to small variations of data. Consider
$$
P : \text{ } \begin{aligned}
\max \text{ }&cx \\
  & Ax\leq b
\end{aligned}
\text{ } D : \text{ } \begin{aligned}
\min \text{ }&yb \\
  & y A =  c\\
  & y\geq 0
\end{aligned}
$$
with optimal solutions $\dot{x},\dot{y}$. Suppose the cost vector is replaced with $c'$. In order to keep having $\dot{x}$ as optimal we must have that the complementary $y'$ relative to $c'$ must remain optimal. Hence if $I$ is the set of active indices
$$
\begin{align}
y'A_{i} = c' \\
y'\geq 0
\end{align}
$$
and if $c'$ is a function of a parameter $\alpha$ we can extract the optimality conditions to be imposed on the parameter.
### Complementary bases

Reconsider the dual problem $P,D$ and let $B \subseteq \{ 1,\dots ,m \}$ be a set of indices such that
$$
\begin{align}
|B| = n \\
\det(A_{B}) \ne 0
\end{align}
$$
We associate with matrix $A_{B}$ the two vector $\dot{x}\in \mathbb{R}^{n}$ and $\dot{y}\in \mathbb{R}^{n}$ defined as follows
$$
\begin{align}
\dot{x}  & = A_{B}^{-1}b_{B}   \\
\dot{y}  & = (\dot{y}_{B}, \dot{y}_{N})   \text{ with } \dot{y}_{B} = c A^{-1}_{B}, \dot{y}_{N} = 0 \text{ and } N = \{ 1,\dots,m \} \setminus B
\end{align}
$$
Such vectors are called **basic solutions** for problems $P$ and $D$ and are associate with the **basis matrix** $A_{B}$

![[slackness condition.png]]

Given a basic solution $\dot{x}$ for $P$, there exists at least one basic solution $\dot{y}$ for $D$ forming with $\dot{x}$ a pair of **complementary basic solutions**. And since basic solutions are characterized by the basis defining them, we can directly extract feasibility and optimality conditions on the basis matrix.
$$
\begin{align}
 & \text{ primal feasible: } b_{N} - A_{N}A^{-1}_{N} b_{B} \geq 0 \\
 & \text{ dual feasible: } cA^{-1}_{B} \geq 0 
\end{align}
$$
We can optimize the optimality conditions in the following theorem which is a consequence of the [[Complementary slackness theorem]]

Let $\dot{x}$ be a basic feasible solution for $P$ and $A_{B}$ a corresponding basis matrix, then $\dot{x}$ is an optimal solution if 
$$
cA^{-1}_{B} \geq 0 \text{ or } b_{N}- A_{N}A_{B}^{-1}b_{B} \geq 0
$$
If $P$ and $D$ have finite optimum, then there exists at least one pair of complementary basic solution, such that $\dot{x}$ is optimal solution of $P$ and $\dot{y}$ is optimal solution of $D$