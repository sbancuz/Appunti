---
tags:
  - parallel_computing
---
Give two sequences $x[1\dots m]$ and $y[1\dots n]$, find a longest subsequence common to them both.

![[LCS.png]]
### Brute force solution

Check every subsequence of $x[1\dots m]$ to see if it is also a subsequence of $[1\dots n]$. The time [[Complexity of an algorithm]] of this approach would be $O(n2^{n})$.
### Simplification

Look at the length of a longest-common subsequence, then we find the LCS itself.
Consider the prefixes of $x$ and $y$.
- Define $c[i,j]=|LCS(x[1\dots i],y[1\dots j])|$
- Then $c[m,n] = |LCS(x,y)|$
$$
c[i,j]=\begin{cases}
c[i-1, j-1]+1  &  x[i]=y[j] \\
\max(c[i-1, j], c[i, j-1])  & \text{otherwise}
\end{cases}
$$
If $z=LCS(x,y)$, then any prefix of $z$ is an $LCS$ of a prefix of $x$ and a prefix of $y$.

Since this algorithm could be expanded to a recursion tree, it means the work to be done is potentially exponential, but we are repeating already solved subproblems. If we reuse previous solutions then this problem becomes polynomial.

```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{LCS}{$x,y,i,j$}
	\If{$c[i][j] = NIL$}
		\If{$x[i] = y[j]$}
			\State $c[i][j] \gets LCS(x,y,i-1,j-1)$
		\Else
			\State $c[i][j] \gets \max(LCS(x,y,i,j-1), LCS(x,y,i - 1,j))$
		\EndIf
	\EndIf
\EndProcedure
\end{algorithmic}\end{algorithm}
```

>[!warning]
>In the exam talk about the spacial complexity as well.

To finally compute the $LCS$ we can just backtrack either with recursion or the memoization matrix and take the resulting string.

![[LCS example.png]]


