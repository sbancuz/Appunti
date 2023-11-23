---
tags:
  - operations_research
---
Consider a bipartite [[Graphs]] $G=(S,T,A)$ with the set of arcs $A \subseteq S\times T$. The problem of the maximum cardinality consists in determining a subset $M$ of maximum cardinality arcs such that $M$ does not contain more than one arc incident on the same node.  This problem can be formulated in terms of maximum flow on an appropriate graph.

![[cardinality flow.png]]

>[!note]
>In this problem the only solutions we admit are only integers, this means that we can find a solution in which flows take value $0$ or $1$.

The [[Augmenting path algorithm]] takes advantage of the fact that in the graph there are unit capacities. In fact, at each iteration the flow augments of exactly one unit. The problem can be solved with [[Complexity of an algorithm]] of $O(m \min \{ |S|,|T| \})$

