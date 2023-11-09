---
tags:
  - parallel_computing
  - coding
---
The quicksort algorithm is a [[Divide and conquer approach]] to sorting an array:
1) Divide the array into 2 sub-arrays around a pivot $x$ such that elements in the lower sub-array $\leq x \leq$ the elements in the upper sub-array
2) Recursively sort the two arrays
3) Trivial
```pseudo
\begin{algorithm}
\begin{algorithmic}
\Procedure{Quicksort}{$A, p, r$}
		\If{$p \lt r$ }
			\State $q \gets $ partition($A, p, r$)
			\State quicksort($A, p, q-1$)
			\State quicksort($A, q + 1, r$)
		\EndIf
\EndProcedure
\end{algorithmic}
\end{algorithm}
```
The first pivot is usually the first element in the array.

The key of this process is the fact the partitioning is done in linear time.
```pseudo
\begin{algorithm}
\begin{algorithmic}
\Procedure{Partition}{$A, p, q$}
	\State pivot $\gets A[p]$
	\State i $\gets p$
	\For{$j \gets p + 1$}
		\If{$A[j] \le$ pivot}
			\State $i \gets i + 1$
			\State exchange $A[i], A[j]$
		\EndIf
	\EndFor
	\State exchange $A[p], A[i]$
	\Return $i$
\EndProcedure
\end{algorithmic}
\end{algorithm}
```
### Worst case

When the input is already sorted in any order the [[Complexity of an algorithm]] is $\Theta(n^{2})$ because all the items when partitioning will be always on one side of the array. In order to avoid this worst case we partition the arrays around a random element.
