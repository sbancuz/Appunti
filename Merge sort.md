---
tags:
  - parallel_computing
  - coding
---

```pseudo
\begin{algorithm}
\begin{algorithmic}
	\Procedure{Merge-sort}{$A, n$}
		\If{$n = 1$} 
			\Return Done
		\EndIf
		\State Recursively sort $A[1 \dots n/2]$ and $A[n/2 + 1 \dots n]$
		\State Merge the 2 sorted lists 
		\EndProcedure
\end{algorithmic}
\end{algorithm}
```
$$
T(n) = \begin{cases}
\Theta(1)  & n = 1 \\
2T\left( \frac{n}{2} \right) + \Theta(n)  &  n > 1
\end{cases}
$$
>[!note]
>We can omit the first $if$  because it's constant time and asymptotically it doesn't matter

It's execution will create a recursion tree that represents the algorithm calls.

![[merge sort.png]]

Since merge sort grows more slowly than insertion sort it should work faster. In practice this isn't always the case. When $n<30$ insertion sort is still faster. This is because the $\Theta$ notation forgets about the scalar terms and $n^{\log_{b}a}$ other costs of the algorithm.
