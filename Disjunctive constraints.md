---
tags:
  - operations_research
---

In the case of a problem is which the feasible region is described by a non-convex polyhedron

![[nc poly.png]]

We can describe the same region as the region described by the union of multiple convex polyhedra  

![[dc poly.png]]

We know that if what we are searching is the intersection, then we'd have to find a solution that optimizes both constraints at the same time, but when finding the optimum for a union we just have to find a solution that satisfies at least one of the groups constraints. This means that one of the two constraints can be made redundant.

![[example ILP.png]]

A particular case in the application of the technique of disjunctive constraints concerns [[Machine task scheduling]] problems.
### Polyhedral methods

Unlike in continuous [[Linear programming]], in ILP the choice of the formulation has a strong influence on the efficiency of the methods of solution, and often proves to be a decisive factor. 

>[!example]-
>![[ILPex.png]]
>The solution given by the standard algorithm is not finite, so how can we find the solution of the ILP? We could try to use the closest integer solution - the blue one - but this isn't clearly the optimal solution. Guessing the solution will not always work, so a solution could be to describe the problem is a different way
>![[ILPEx2.png]]
>First things first, we notice that the feasible region is the same so we can say that the two formulation are equivalent. The second thing we notice is that the second formulation has all vertices corresponding with feasible solution for the ILP problem, this is useful because in [[Linear programming]] if a finite optimum exists, then at least one vertex of the polyhedron is optimal and it also implies that the solution we will obtain will be optimal and integer.

Given a finite set of points $S$, the **convex envelope** of $S$, denoted $conv(S)$, is the smallest convex polyhedron containing all points of $S$. Now consider
$$
P : \text{ } \begin{aligned}
\min \text{ }&cx \\
  & Ax = b \\
  & x \in \mathbb{Z}^{n}
\end{aligned}
\text{ } P' : \text{ } \begin{aligned}
\min \text{ }&cx \\
  &x \in conv(\{ Ax = b,  x \in \mathbb{Z}^{n}\}) 
\end{aligned}
$$
if we envelop $P$ in $P'$ and find its optimal solution, then the result will be optimal even for $P$. The problem is in the feasibility and efficiency of this method. Creating an envelope may be impossible - like in the case of the travelling salesperson problem - or it may require an exponential number of constraints. 

There are cases in which the polyhedron $\dot{P}: \{ Ax =b, x\geq 0 \}$ coincides with $P'$. This happens when each vertex of $\dot{P}$, and therefore each of its bases, has integer components - called the **integrality property**. This types of problem can be easy to manage.
### Theorem

If $A$ and $b$ have integer component and $A$ is a [[Matrix#Unimodular matrix]] then all basic solution of the problem 
$$
\text{ } \begin{aligned}
\min \text{ }&cx \\
  & Ax \geq b \\
  & x \in \mathbb{Z}^{n}
\end{aligned}
$$
have integer components. If A is totally [[Matrix#Unimodular matrix]]  then also this problem has integer solution
$$
\text{ } \begin{aligned}
\min \text{ }&cx \\
  & Ax \leq b \\
  & x \in \mathbb{Z}^{n}
\end{aligned}
$$
As a consequence of the [[Matrix#Unimodular matrix]], the incidence matrix of both a biparte undirected graphs and [[Graphs#Directed graphs]] are TU. Therefore [[Flow optimization problems]] and [[Paths#Shortest path problem]] all have integer solutions.

The polyhedral or **cutting plane** method do nothing but iteratively refine the polyhedron of the convex envelope where we think the optimal solution is situated. If $\dot{P}$ is a LP problem that we suppose to admit finite optimal solution $\dot{x}$, then if $\dot{x}$ has all integer components then it coincides with the optimal solution of $P$, otherwise we can define the formulation of $\dot{P}$ by adding more constraints

A **valid inequality** is of type $gx\leq\gamma$ and a valid **cut** is $g\dot{x}>\gamma$. Therefore, if we detect a cutting plane for $\dot{P}$ and its fractional optimal solution $\dot{x}$, we can add such inequality to the formulation and interate the procedure.

```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{CuttingPlaneMehtod}{}
	\State optimal$\gets$\false
	\While{$\lnot$optimal}
		\State Solve($\dot{P}, \dot{x}$)
		\If{IsAllIntegers($\dot{x}$)}
			\State optimal $\gets$ \true
		\else
			\State GenerateCut($g, \gamma$)
			\State AddCut($\dot{P}, g, \gamma$)
		\EndIf
	\EndWhile
\EndProcedure
\end{algorithmic}\end{algorithm}
```
Consequently we only need a method to generate effective cutting planes.
### Chvatal inequality 

Given a vector $u = [u_{i}]\geq 0$ each inequality $g(x) \leq \gamma$ with 
$$
g_{j} = \lfloor \sum u_{i} A_{ij} \rfloor \qquad \gamma = \lfloor \sum u_{i} b_{i} \rfloor
$$
is a valid inequality.

Unfortunately this method does not provide constructive tools to create a valid inequality that also is a cut. 
### Gomory cuts

This is a general method of generating cuts for any integer linear programming problem starting from the fractional optimal solution of the problem in which integrity constraints were left out.

Let $\dot{x}$ be a basic solution ([[Linear programming#Complementary bases]]) of $\dot{P}$, hence $\dot{x}_{B}=A_{B}^{-1}b$ and $\dot{x}_{N} = 0$. We also call $\dot{b} = A_{B}^{-1}b$ and $\dot{A}=A_{B}^{-1}A_{N}$. If $\dot{x}_{B}$ has all integer components, then the solution $\dot{x}$ is optimal also for $P$. Otherwise there exists a component $h$ such that $\dot{x}_{h}$ has non integer values. Let $t$ be the constraint corresponding to $h$
$$
x_{h} + \sum \dot{a}_{tj}x_{j} = \dot{b}_{t} \implies x_{h} = \lfloor\dot{b}_{t}\rfloor
$$
### Implicit enumeration methods

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

