---
tags:
  - operations_research
---
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
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{AugmentingPaths}{$G,s,t,x$}
	\For{$(i,j)\in A$}
		\State $x[i,j] \gets 0$
	\EndFor
	\While{$P[t] \ne \emptyset$}
		\State $G_R \gets $ ResidualGraph($x$)
		\State GraphSearch($G_R,s,P$)
		\If{$P[t] \ne \emptyset$}
			\State AugmentFlow($P,x$)
		\EndIf
	\EndWhile
\EndProcedure

\Procedure{AugmentFlow}{$P, x$}
	\State $\theta \gets$ ResidualCapacity($P,x$)
	\For{$(i,j)\in A$}
		\If{$(i,j) \in A^+$}
			\State $x[i,j] \gets x[i,j] + \theta 0$
		\Else
			\State $x[i,j] \gets x[i,j] - \theta 0$
		\EndIf	
	\EndFor
\EndProcedure

\Procedure{ResidualCapacity}{$P$}
	\Return $\min \{u_{ij} - x[i,j]: (i,j) \in A^+ \cap P, x[i,j]: (i,j) \in A^- \cap P\}$
\EndProcedure
\end{algorithmic}\end{algorithm}
```

>[!example]-
>Given this graph where a feasible flow is show as well
>![[flow ex1.png]]
>We can construct the residual graph by testing, arc by arc, if the flow can be augmented by introducing an arc of $A^{+}$ and/or diminished by introducing an arc of $A^{-}$
>![[flow 3.png]]
>
>The graph search now finds a first path $s,2,4,t$ with $\theta = \min \{ 3-1,3,4 \} =2$ and because this is composed of arcs of $A^{+}$ the new flow is obtained by summing $\theta$ to the flow already exiting the path arcs.
>
>By applying again the search from node $s$ we find $s,1,3,2,4,t$ with $\theta = 1$. Note that in this path we use $A^{-}$. The flow now implies an augmentation of $1$ on $(s,1), (1,3), (2,4), (4,t)$ and a diminution of $1$ unit on $(2,3)$. On the resulting graph is not possible to find again a path from $s$ to $t$, this means that there is a cut.
> ![[flow4.png]]
> It should be noted that in the detected cut the flow non the arcs of $A^{+}(S,T)$ is placed at the upper capacity, whereas on the arcs of $A^{-}(S,T)$ it is at $0$.
> ![[flow 5.png]]


