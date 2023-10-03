---
tags:
  - parallel_computing
  - coding
---
The sum of all the elements in an array can be done in $O(\log n)$ time in [[Parallel machine model]]

```pseudo
\begin{algorithm}
\begin{algorithmic}
	\Procedure{Logarithmic-sum}{$A$}
		\For{H = 1 $ \to \log n$ }
			\If{$i \le \frac{n}{2^k}$}
				\State $B(i) \gets B(2i-1) + B(2i)$
			\EndIf
		\EndFor
	\EndProcedure
\end{algorithmic}
\end{algorithm}
```
It's performance is:
- $T^{*}(n) = n$
- $T_{P=N}(n) = 2+\log n$
- $SU_{P} = \frac{n}{2+\log n}$
- $COST = P (2+\log n)$
- $E_{P} = \frac{1}{\log n}$

