---
tags:
  - operations_research
---
```pseudo
\begin{algorithm}
\begin{algorithmic}
\Procedure{GraphSearch}{$G, P, d$}
	\For{$i \gets 2 \dots n$}
		 \State $P[i] \gets 0$
		 \State $d[i] \gets \infty$
	\EndFor
	\State $P[1] \gets 1$
	\State $d[1] \gets 0$
	\For{$i \gets 1 \dots n- 1$}
		\For{$(i,j)\in FS(i)$}
			\If{$d[i] + c_{ij} \lt d[j]$}
				\State $P[j] \gets i$
				\State $d[j] \gets d[i] + c_{ij}$
			\EndIf
		\EndFor
	\EndFor		
\EndProcedure
\end{algorithmic}
\end{algorithm}
```
This [[Complexity of an algorithm]] for this is linear to the number or arcs in the graph.