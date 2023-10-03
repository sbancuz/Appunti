---
tags:
  - parallel_computing
  - coding
---
There aren't any comparisons during this sorting. The idea is to count the digits of the element of the array and then reconstruct it in $O(n)$ time

```pseudo
\begin{algorithm}
\begin{algorithmic}
\Procedure{Counting-sort}{$A$}
	\For{$i \gets 1$ to $k$}
		\State $C[i] \gets 0$
	\EndFor
	\For{$j \gets 1$ to $n$}
		\State $C[A[j]] \gets C[A[j]] + 1$
	\EndFor
	\For{$i \gets 2$ to $n$}
		\State $C[i] \gets C[i] + C[i - 1]$
	\EndFor
	\For{$j \gets n$ downto $1$}
		\State $B[C[A[j]]] \gets A[j]$
		\State $C[A[j]] \gets C[A[j]] -1$
	\EndFor
\EndProcedure
\end{algorithmic}
\end{algorithm}
```

This is a [[Stable sorting algorithm]]. The problem with this algorithm is it's memory footprint, it consumes as much as the biggest element of the array.