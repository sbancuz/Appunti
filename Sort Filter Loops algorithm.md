---
tags:
  - databases
---
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{SFS}{$D$}
	\State $S = D$ sorted by a monotone function of $D$ attributes
	\State $W \gets \emptyset$
	\For{$p \in S$}
		\If{$p \nprec p' \in W$}
			\State Add $p$ to $W$
		\EndIf 
	\EndFor 
	\Return $W$
\EndProcedure
\end{algorithmic}\end{algorithm}
```

This is the same as [[Block Nested Loop algorithm]] but the presorting yields a much better performance for large datasets.