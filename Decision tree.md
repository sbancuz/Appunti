---
tags:
  - operations_research
---
Decision trees represent the set of the solutions of a [[Integer linear programming]] problem. Each node of the tree corresponds to a subproblem in which some variables have values that are fixed in advance.

![[decision tree2.png]]

The number of nodes at level $i$ are $2^{i}$, this means the [[Complexity of an algorithm]] for finding the optimal solution is exponential. But we don't necessarily need to check all branches of the tree to find the optimal solution because we can discard some nodes when it gets detected that it is unfeasible, thus eliminating the whole subtree from the computation. A second criterion allowing to reduce the extend of the enumeration is related to the value of solutions - [[Minimax algorithm]] - thus removing whole portions of the computation just because we know we already found a better result and the computation wont ever yield a better one.

![[burglar.png]]

These ideas can be implemented in the **branch and bound** algorithm
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{BranchAndBound}{$P,v$}
	\State $b \gets $Bound($P, x, unfeasible$)
	\If{isInt($x$)}
		\Return b
	\Elif{unfeasible}
		\Return $-\infty$
	\Elif{$b>v$}
		\State Branch($P, x, P_1, \dots, P_k$)
		\For{$i \gets 1 \dots k$}
			\State $t \gets $ BranchAndBound($P_i, v$)
			\If{$t > v$} 
				\State $v \gets t$
			\EndIf
		\EndFor
	\EndIf
\EndProcedure
\end{algorithmic}\end{algorithm}
```
The **Bound** function provides a higher estimation of the optimal solution value of the subproblem $P$, returning also a solution $x$ and a logical value that is $true$ if a subproblem $P$ admits no solution. Also if $unfeasible$ is $true$ then we can stop the computation on the branch. The **branch** just passes the solution $x$ to the various subproblems, thus branching the computation. 

A further characterization of the branch and bound is the criterion according to which we choose the next node of the enumeration tree to be expanded. In general we can distinguish:
- **best first** -> [[Search problem#Breadth-First Search]]
- **depth first** -> [[Search problem#Depth First Search]]

