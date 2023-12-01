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

