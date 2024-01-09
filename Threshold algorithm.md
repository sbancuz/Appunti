---
tags:
  - databases
---
Algorithm that computes the ranking of some ranked lists with some **monotone** function
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{TA}{$k, S, R_n$}
	\While{\true}
		\State $objs \gets $ sorted access in $\textbf{parallel}$ in each list $R_i$
		\For{$obj \in objs$}
			\State $s_j \gets $ random access in other list $R_j$
		\EndFor 
		\State $score \gets $ overall score
		\If{$score$ is the $k$-th highest}
			\State $buf \gets obj$
		\EndIf 
		\State $s_{Li}$ is the last score seen under sorted access for $R_i$
		\State $T \gets S(s_{L1}, \dots, s_{Lm})$
		\If{the score of the $k$-th obj is $\lnot$ worse than $T$}
			\Return the current top $k$ objects
		\EndIf 
	\EndWhile 
\EndProcedure
\end{algorithmic}\end{algorithm}
```
This algorithm is instance optimal among all algorithms that use random and sorted access and it's stopping criterion depends on the scoring function.

>[!example]-
>![[TA algo example.png]]