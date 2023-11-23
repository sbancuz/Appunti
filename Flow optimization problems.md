---
tags:
  - parallel_computing
---
Given a digraph $G$ with $u_{ij}$ capacities associated with arcs, the maximum flow problem consists in finding the maximum amount of flow that can be sent from node $s$ to $t$, while respecting arc capacities as well as the fact that flow must not be dispersed at intermediate nodes.

![[flow ex.png]]

The first group of constraint - associated with the nodes except $s,t$ - are called **flow conservation constraints**  and the second group - associated with the arcs - are called **capacity constraints**.
### Cuts

A partition of the nodes into two subsets $S$ and $T$ is called s-t cut. The arcs crossing the cut are themselves partitioned into two subsets:
- directed arcs -> from S to T
- inverse arcs -> from T to S

Given a cut, the quantity of flow crossing the cut is given by the quantity of flow traversing direct arcs minus the quantity of flow traversing inverse arcs and its capacity is the sum of capacities of directed arcs.

>[!tip]
>It is obvious that the cut that is most limiting is the one of minimum capacity

The overall complexity is $O(nm^{2}\log n)$
### Maximum flow problem

![[Augmenting path algorithm]]

![[Edmonds-Karp algorithm]]

![[Maximum cardinality flow]]
### Minimum cost flow problem

The minimum cost flow problem can be seen as a generalization of both the maximum flow and shortest path. A network flow is specified by a digraph $G=(N,A)$, with each node $i\in N$ we associate a value $b_{i}$ called the **balance** of the node, and with each arc $(i,j)$ we associate the unit **cost** $c_{ij}$ and the **capacity** $u_{ij}$ limiting the maximum quantity of flow that can transit. There can be 3 types of nodes:
- transshipment node -> $b_{i} = 0$
- source node -> $b_{i} < 0$
- sink node -> $b_{i} > 0$

>[!info]
We also assume that the global network balance is null: $\sum b_{i} = 0$

![[Negative cycle elimination algorithm]]
### Feasible starting flow

The computation if a feasible flow can be performed in polynomial time by means of a maximum flow algorithm on an appropriate graph. 
### Multi-commodity flow problems

The problems characterized so far are homogeneous in respect to the flow. 