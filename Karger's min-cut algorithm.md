---
tags:
  - parallel_computing
---
Let $G = (V,E)$ be a connected undirected graph. Let $n = |V|$, $m = |E|$. For $S \subset V$, the set $\delta(S) = \{ (u,v) \in E : u \in S, v \in S' \}$ is a cut since their removal from $G$ disconnects $G$ into more than one component. Find the minimum sized cut.

![[mimncut.png]]

Traditionally it was solved by running the minimum st-cut problem (complexity of $O(nm \log(\frac{n^{2}}{m}))$) $n-1$ times. In the minimum st-cut is to find the set $S$ which minimize the size of the cut.

1) The first thing to do is to transform the graph in a multiedge graph (it allows multiple edges between 2 nodes).
2) Then we pick an edge and we contract it.
![[contract edge.png]]
3) Repeat until we have 2 collapsed nodes, then the remaining edge is the minimum cut
#### Lemma

The minimum cut size of the graph is found with $Pr(cut)\geq \frac{1}{{n}\choose{2}}$

In order to boost the probability of success, we simply run the algorithm $l$ times. This improves the probability to $1 - e^{-l}$  and it takes $O(n^{2})$ time [[Complexity of an algorithm]]

#### Improved algorithm

An improvement over this algorithm is to repeat until the graph is reduced to have at least $\frac{n}{\sqrt{ 2 } + 1}$ vertices then recursing on a graph. The idea is that the initial contraction is very unlikely to contract to a minimum cut and the further we go this probability improves. So for a minimum cut, the probability that it survives is at least ${{l}\choose {2}}/{{n\choose{2}}}$ and for $l = \frac{n}{\sqrt{ 2 }}$ we have a probability of $\frac{1}{2}$ of succeeding. The new complexity is $O(\log^{2}n)$ and the probability of success is $\geq 1-\frac{1}{poly(n)}$