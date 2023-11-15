---
tags:
  - distributed_systems
---
This is a method to compute the dependency graph in a certain moment. 

We draw an arrow between 2 checkpoints $c_{ix}$ and $c_{iy}$ and if either:
- $i =j$ and $y = x+ 1$
- $i \neq j$ and a message is sent from $I_{ix}$ to $I_{iy}$

The recovery line is computed by marking the nodes corresponding to the failed state and then marking all those which are reachable from one of them. These marked nodes will be deleted and the state of the system will be restored to the last unmarked state. 