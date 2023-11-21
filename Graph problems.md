---
tags:
  - operations_research
---
Given a [[Graphs]], we define a [[Model optimization problems]] in which a solution is a sub graph or [[Paths]] that minimizes/maximizes the sum of all the weights.
$$
\begin{align}
\text{Sets: } &  N, A \\
\text{Parameters: } &  w_{ij}, \forall {ij \in A}  {}  \\
\text{Variables: } & x_{ij} = \begin{cases}
1  & \text{if } ij \in A \\
0  &  \text{otherwise}
\end{cases}\\
\text{Obj func: } &  \min \sum w_{ij} x_{ij} \\
\text{Constraint: } &  \sum_{ij\in A \atop i \in S,j\in N \setminus S}  x_{ij} \geq 1\\
\end{align}
$$
### Kruskal algorithm

To find the minimum spanning tree for a weighted, undirected graph we use
```pseudo
\begin{algorithm}
\begin{algorithmic}
\Procedure{Kruskal}{G}
	\State sortWeights($G$)
	\State $A' \gets \emptyset$
	\While{|$A'$|$ \ne n-1$}
		\If{doesInduceCycle($A' \cup \{i,j\}$)}
			\State $A' \gets A' \cup \{i,j\}$
		\EndIf
	\EndWhile
\EndProcedure
\end{algorithmic}
\end{algorithm}
```
But how do we check if a sub-graph has a loop? We use a [[Find union]] that allows to do this check in almost constant time [[Complexity of an algorithm]].

There are also other algorithms like [Boruvka's](https://en.wikipedia.org/wiki/Bor%C5%AFvka%27s_algorithm) that was designed much earlier
