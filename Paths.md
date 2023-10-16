---
tags:
  - operations_research
---
```math
||{"id":1117737196070}||


```
### Existing path problem

In this simple example, given a [[Graphs]] of a city in which the intersections are the nodes and the street represent the arcs, we need to check if all nodes can be reached from all other nodes. These arcs may be uni or bi-directional.

>[!tip]
The length of the path must be at most $n - 1$.

![[Graph search algorithm]]
#### Lemma

Given a graph, either there exists a directed path that goes from one node to another or there exists a cut where all nodes from the cut side can go to the origin side.

### Shortest path problem

If $G$ is acyclic we can define the topological order starting from the initial node, which is a node without any input arcs, then we repeat the process always selecting nodes with only 1 input. When we are done with all the nodes we can define a simple recursive algorithm that can find the shortest path.
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

