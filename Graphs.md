---
tags:
  - operations_research
---
A graph is a collection of nodes and arcs interconnected with each other. These arcs may have an associated weight that is represented by some non negative constant.

![[graph.png]]
### Path

We can also define a **path** as the sequence of consecutive arcs that link 2 nodes with each other. A **simple path** is special path that doesn't have repeated arcs, and an **elementary path** doesn't repeat nodes. 
### Cycle

A **cycle** that is a closed path. Some special types of cycles are:
 - elementary cycle that has no repeated nodes
 - Hamiltonian cycle that visits all the nodes
 - simple cycles that don't repeat arcs
 - Eulerian tours that visit all nodes once
### Directioned graphs 

Given a graph $G = (N,A)$ with $N$ representing all the nodes and $A$ the arcs a directed graph is a graph there is a distinction between 2 arcs that connect the same 2 nodes.
