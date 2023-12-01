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

