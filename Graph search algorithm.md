---
tags:
  - operations_research
  - coding
---
```pseudo
\begin{algorithm}
\begin{algorithmic}
\Procedure{GraphSearch}{$G, s, P$}
	\For{$i \in N$}
		 \State $P[i] \gets 0$
	\EndFor
	\State $P[s] \gets s$
	\State $Q \gets \{s\}$
	\While{$Q \ne \emptyset$}
		\State $i \gets $ getFrom($Q$)
		\State $Q \gets Q \setminus \{i\}$
		\For{$(i,j)\in FS(i)$}
			\If{$P[j] = 0$}
				\State $P[j] \gets i$
				\State $Q \gets Q \cup \{j\}$
			\EndIf
		\EndFor
	\EndWhile		
\EndProcedure
\end{algorithmic}
\end{algorithm}
```

This algorithm has a time [[Complexity of an algorithm]] of $O(n^{2})$ in the worst case, but in general, the average case is $O(m)$ where $|A| = m$
