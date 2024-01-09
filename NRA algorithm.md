---
tags:
  - databases
---
The Non Random Access returns the top $k$ objects, but their scores might be uncertain. The idea is to maintain, for each object $o$ retrieved by sorted access, a **lower bound** $S^{-}(o)$ and **upper bound** $S^{+}(o)$ on its score.
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{NRA}{$k, S, R_n$}
	\While{$S(B[k]) < \max\{\max\{S^+(B[i]), i > k\}, S(t)\}$}
		\State Make sorted access to each list
		\State Store in $B$ each $o$ and maintain $S^-(o)$ and $S^+(o)$ and threshold $t$ 
	\EndWhile 
	\Return the top $k$ elements
\EndProcedure
\end{algorithmic}\end{algorithm}
```
>[!example]-
>![[NRA ex.png]]