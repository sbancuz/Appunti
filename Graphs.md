---
tags:
  - operations_research
---
A graph $G$ is a collection of nodes $N$ and arcs $A$ interconnected with each other. These arcs may have an associated weight that is represented by some non negative constant.

![[graph.png]]
### Directed graphs 

Given a graph $G = (N,A)$ with $N$ representing all the nodes and $A$ the arcs a directed graph is a graph there is a distinction between 2 arcs that connect the same 2 nodes.
### Trees

A tree is a connected graph that does not contain a [[Paths#Chain|chain]]. The spanning tree $T$ of $G$ if all nodes of $G$ are head or tail of arcs of $T$
### Adjacency matrix

A graph can also be represented as a square matrix with a each row/column representing each node of graph. The coefficient $ad_{ij}$ is equal to $q$ iff there is an arc that connects the node.

>[!note]
>Each non-zero element represents the corresponding forward-star of the [[Paths]] 

