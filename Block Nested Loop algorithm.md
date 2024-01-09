---
tags:
  - databases
---
This is an algorithm to compute the [[Ranking queries#Skyline queries]] 

```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{BNL}{$D$}
	\State $W \gets \emptyset$
	\For{$p \in D$}
		\If{$p \nprec p' \in W$}
			\State Remove from $W$ the point dominated by $p$
			\State Add $p$ to $W$
		\EndIf 
	\EndFor 
	\Return $W$
\EndProcedure
\end{algorithmic}\end{algorithm}
```

The [[Complexity of an algorithm]] is $O(n^{2})$ where $n = |D|$ so it's slow.

