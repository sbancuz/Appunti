---
tags:
  - parallel_computing
---
To find the the i-th number in an array using a naive implementation the [[Complexity of an algorithm]] is the order of $T(n) = \Theta(n\log n)$ since we just sort using [[Merge sort]] or [[Heapsort]] and just retrieve the element.
### Randomized [[Divide and conquer approach]]

```pseudo
\begin{algorithm}
\begin{algorithmic}
\Procedure{randSelct}{$A, p, q, i$}
	\If{$p = q$}
		\Return $A[p]$
	\EndIf
	\State $r \gets $ randPartition($A, p, q$)
	\State $k \gets r- p + 1$
	\If{$i = k$}
		\Return $A[r]$
	\EndIf
	\If{$i \lt k$}
		\Return randSelect($A, p, r - 1, i$)
	\Else
		\Return randSelect($A,r+1,q,i -k$)	
	\EndIf
\EndProcedure
\end{algorithmic}
\end{algorithm}
```

>[!note]
randPartition is the function used in [[Quicksort]]

In the lucky case we have a complexity of $T(n) = \Theta(n)$ and in the unlucky case we have $T(n^{2})$. If, just like for the quicksort, we randomize the selection of the pivot we should land almost always in the lucky case.
### Worst case linear time

![[algo.png]]