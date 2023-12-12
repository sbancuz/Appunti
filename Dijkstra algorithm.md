---
tags:
  - operations_research
---
```pseudo
\begin{algorithm}
\begin{algorithmic}
\Procedure{Dijkstra}{$G, r, P, d$}
	\For{$i \gets 2 \dots n$}
		 \State $P[i] \gets 0$
		 \State $d[i] \gets \infty$
	\EndFor
	\State $P[r] \gets r$
	\State $d[r] \gets 0$
	\State $Q \gets \{r\}$
	\While{$Q \ne \emptyset$}
		\State $i \gets $ selectFromWithMinD($Q$)
		\State $Q \gets Q \setminus \{i\}$
		\For{$(i,j)\in FS(i)$}
			\If{$d[i] + c_{ij} \lt d[j]$}
				\State $P[j] \gets i$
				\State $d[j] \gets d[i] + c_{ij}$
				\State $Q \gets Q \cup \{j\}$
			\EndIf
		\EndFor
	\EndWhile	
\EndProcedure
\end{algorithmic}
\end{algorithm}
```

Dijkstra algorithm is a very efficient algorithm, but it cannot find the shortest path if there are negative weight path. To fix this, although slowing the algorithm down, is to select the indices with a FIFO policy from $Q$. The Global complexity is $O(V^{2})$ and it can be brought down to $O(E\log V)$
