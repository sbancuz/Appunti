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

