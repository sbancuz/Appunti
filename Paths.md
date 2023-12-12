---
tags:
  - operations_research
---

We can define a **path** as the sequence of consecutive arcs that link 2 nodes with each other. A **simple path** is special path that doesn't have repeated arcs, and an **elementary path** doesn't repeat nodes. 
```math
||{"id":1117737196070}||


```
### Cycle

A **cycle** that is a closed path. Some special types of cycles are:
 - elementary cycle that has no repeated nodes
 - Hamiltonian cycle that visits all the nodes
 - simple cycles that don't repeat arcs
 - Eulerian tours that visit all nodes once
### Chain

A chain is a type of digraph such that every node $a_{k}$ is $(i_{k}, i_{k+1})$ and a closed chain is also constrained to have $a_{last} = (i_{last}, i_{1})$ 
### Existing path problem

In this simple example, given a [[Graphs]] of a city in which the intersections are the nodes and the street represent the arcs, we need to check if all nodes can be reached from all other nodes. These arcs may be uni or bi-directional.

>[!tip]
The length of the path must be at most $n - 1$.

![[Graph search algorithm]]
#### Lemma

Given a graph, either there exists a directed path that goes from one node to another or there exists a cut where all nodes from the cut side can go to the origin side.
### Shortest path problem

If $G$ is acyclic we can define the <span class="ob-html-comment" id="comment-d7d9da8e-d685-4788-8210-80ac171f177d" data-tags="[comment,]"><span class="ob-html-comment-body">if (i,j) in A then i less then j </span>topological order</span> starting from the initial node, which is a node without any input arcs, then we repeat the process always selecting nodes with only 1 input. When we are done with all the nodes we can define a simple recursive algorithm that can find the shortest path.
$$
d[i] = \min\{d[j] + c_{ij}: (ij) \in BS(i)\}
$$

![[Shortest path algorithm in acyclic graph]]
$$
\text{objective function } = \begin{cases}
min \sum_{ij \in A} c_{ij}x_{ij} \\
\sum_{sj \in FS(s)} x_{sj} = 1 \\
\sum_{it \in BS(t)} x_{it} = 1 \\
\sum_{ji \in BS(i)} x_{ji} - \sum_{ij \in FS(i)} x_{ij} = 0 
\end{cases}
$$

If the graph is cyclic it means that nodes and arcs are examined only once according to the order when a node $i$ is considered $d[i]$ has the final value.
$$
c_{ij} \ge 0, \forall {(i,j)}\in A 
$$
![[Dijkstra algorithm]]

