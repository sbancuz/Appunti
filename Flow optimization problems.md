---
tags:
  - parallel_computing
---
Given a digraph $G$ with $u_{ij}$ capacities associated with arcs, the maximum flow problem consists in finding the maximum amount of flow that can be sent from node $s$ to $t$, while respecting arc capacities as well as the fact that flow must not be dispersed at intermediate nodes.

![[flow ex.png]]

The first group of constraint - associated with the nodes except $s,t$ - are called **flow conservation constraints**  and the second group - associated with the arcs - are called **capacity constraints**.
### Cuts

A partition of the nodes into two subsets $S$ and $T$ is called s-t cut. The arcs crossing the cut are themselves partitioned into two subsets:
- directed arcs -> from S to T
- inverse arcs -> from T to S

Given a cut, the quantity of flow crossing the cut is given by the quantity of flow traversing direct arcs minus the quantity of flow traversing inverse arcs and its capacity is the sum of capacities of directed arcs.

>[!tip]
>It is obvious that the cut that is most limiting is the one of minimum capacity
### Augmenting path algorithm

Given a flow problem with a feasible solution, we test if it's improvable. In order to discover if such flow augmentation is practicable, we introduce the **residual graph of a flow** $\dot{x}$.

Given a graph $G = (N,A)$ with capacity on the arcs $u$ and $a$ feasible flow $\dot{x}$, we define the residual graph 
$$
G_{R}(\dot{x}) = (N, A(\dot{x}))
$$
where the arcs are defined as follows
$$
\begin{align}
A(\dot{x})  & = A^{+}(\dot{x}) \cup A^{-}(\dot{x}) \\
A^{+}(\dot{x})  & = \{ (i,j) : (i,j) \in A, \dot{x}\leq u_{ij} \}  \\
A^{-}(\dot{x})  & = \{ (i,j) : (i,j) \in A, \dot{x}\geq 0 \} 
\end{align}
$$
>[!example]-
>Given this graph where a feasible flow is show as well
>![[flow ex1.png]]
>We can construct the residual graph by testing, arc by arc, if the flow can be augmented by introducing an arc of $A^{+}$ and/or diminished by introducing an arc of $A^{-}$
>![[flow 3.png]]

```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{Augmenting\_paths}{$G,s,t,x$}
	\For{$(i,j)\in A$}
		\State $x[i,j] \gets 0$
	\EndFor
	\While{$P[t] \ne \emptyset$}
		\State $G_R \gets $ Residual\_graph($x$)
		\State Graph\_search($G_R,s,P$)
		\If{P[t] \ne \emptyset}
			\State Augment\_flow($P,x$)
		\EndIf
	\EndWhile
	\State Augment_flow($P,x$)
	\State $\theta \gets$ Residual\_capacity($P,x$)
	\For{$(i,j)\in A$}
		\If{$(i,j) \in A^+$}
			\State $x[i,j] \gets x[i,j] + \theta 0$
		\Else
			\State $x[i,j] \gets x[i,j] - \theta 0$
		\EndIf	
	\EndFor
	\State
\EndProcedure
\end{algorithmic}\end{algorithm}
```



