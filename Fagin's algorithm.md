---
tags:
  - databases
---
Algorithm used to combine ranked lists with some scoring function $S$.
```pseudo
\begin{algorithm}\begin{algorithmic}
	\Procedure{Fagin}{$k, S, R_n$}
	\State Extract $k$ common objects by sorted access in each list
	\For{$object \in extracted$}
		\State Compute the score by making random accesses when needed
	\EndFor
	\Return The best $k$ objects  
\EndProcedure
\end{algorithmic}\end{algorithm}
```

The [[Complexity of an algorithm]] is sub-linear in the number of $N$ objects $O(N^{(m-1)/m}k^{1/m})$. The stopping criterion in **independent** of the scoring function but is not instance optimal.

>[!example]-
>![[Fagin algo.png]]