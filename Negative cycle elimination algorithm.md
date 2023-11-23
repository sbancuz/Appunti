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

![[neg flow.png]]

The only way of modifying the solution without violating the flow conservation is to vary the flow on a **cycle** by an identical quantity $\theta = \min \{ u_{ij} - x_{ij}: (a,j) \in A^{+} \cap C, x_{ij}: (a,j) \in A^{-} \cap C,  \}$ and the flow is updated according to 
$$
x'_{ij} = \begin{cases}
x_{ij}+ \theta  & (i,j) \in A^{+}\cap C \\
x_{ij} - \theta & (i,j) \in A^{-}\cap C \\
x_{ij}  & \text{ otherwise }
\end{cases}
$$
This means that there is an improvement in the solution iff a cycle $C$ has sum of negative residual cost. A circulation is **simple** if the arcs $i(i,j)$ in which $x_{ij}>0$ detect a cycle.
### Flow decomposition theorem

Consider a graph $G$
$$
\min \sum c_{ij}x_{ij} = -\sum_{(i,j) \in FS(i)} x_{ij} + \sum_{(i,j) \in BS(i)} x_{ij} = b_{i}
$$
Let there be a feasible flow $\dot{x}$ and an optimal flow $\ddot{x}$. There exist $k$ simple circulations $x_{1},\dots,x_{k}$ allowing to transform $\dot{x}$ into $\ddot{x}$ such that $\dot{x}+x_{1}+\dots+x_{k}=\ddot{x}$ 

>[!corollary]
>The number $k$ of simple circulations is limited by the number $m$ of arcs of $G$

>[!Corollary]
>The residual cost of cycles $C_{1},\dots,C_{k}$ is smaller than or equal to zero

This means that the optimality condition is: The feasible flow $\dot{x}$ is optimal iff $G_{R}(\dot{x})$ does not contain cycles who sum of residual cost is negative.

```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{NegativeCycleElimination}{$G,x$}
	\State $G_R \gets $ ResidualGraph($x$)
	\While{$\exists$ negative clycle $C \in G_R$}
		\State updateFlow($x,C$)
		\State updateResidualGraph($x$)
	\EndWhile
\EndProcedure
\end{algorithmic}\end{algorithm}
```

