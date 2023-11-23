---
tags:
  - operations_research
---
Let us consider a flow $\dot{x}$ being a feasible solution of the problem, we can define the residual graph $G_{R}(\dot{x})$ associated with it. In the minimum cost flow case the cost is essential to evaluate to decide whether a flow variation is advantageous, therefore with each arc of the residual graph we can associate a **residual cost** $g_{ij}$ that quantifies the effect on the objective function of a unitary variation of the flow
$$
g_{ij} = \begin{cases}
c_{ij}  & (i,j) \in A^{+} \\
-c_{ij} & (i,j) \in A^{-}
\end{cases}
$$
A route on the residual graph corresponds to a possible variation of the flow $\dot{x}$ according to the same rules we saw with the maximum flow.