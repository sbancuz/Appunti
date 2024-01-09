---
tags:
  - databases
---
Each node is stored in a block, and in general each node has a large number of descendants and leaf nodes.

![[b+tree.png]]

Each node can hold up to $N-1$ search keys. At least $\left\lceil\frac{(N-1)}{2}\right\rceil$ key values should be present in each node and all search keys are sorted.
### Search

At each intermediate node:
- if $V < K_{1}$ follow $P_{1}$
- if $V \geq K_{N-1}$ follow $P_{N}$
- otherwise, follow $P_{j-1}$ such that $K_{j} \leq V < K_{j+1}$

And it's complexity is $O(h)$
