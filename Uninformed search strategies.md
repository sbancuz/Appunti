---
tags:
  - artificial_intelligence
---
An uninformed search algorithm is given no clue about how close a state is to the goal, for example if given a graph, the algorithm doesn't know what is the best first step to reach its goal.
#### Breadth-First Search

When all actions have the same cost, we can use the breath first search. It's a search algorithm in which all the nodes at level $k$ of the search tree must be selected before selecting any node at level $k+1$. It always selects the node with minimum depth.
```pseudo
   \begin{algorithm}
    \begin{algorithmic}
      \PROCEDURE{Breadth-first-search}{$problem$} 
		\STATE $node \gets$Node($problem.$INITIAL)
		\If{$problem.$IsGoal($node$.STATE)} \return $node$
		\EndIf
		\State $frontier \gets$ a FIFO queue, with $node$ as an element
		\State $reached \gets \lbrace problem.$INITIAL $\rbrace$ 
		\While{$\textbf{not}$ IsEmpty($frontier$)}
			\State $node \gets $Pop($frontier$)
			\For{$\textbf{each}$ child $\textbf{in}$ Expand($problem, node$)}
				\State $s \gets child.$STATE
				\If{$problem.$IsGoal($s$)} \Return $child$
				\EndIf
				\If{$s$ is not in $reached$}
					\State add $s$ to reached
					\State add $child$ to frontier
				\EndIf
			\EndFor
		\EndWhile
		\Return $failure$
      \ENDPROCEDURE
      \end{algorithmic}
    \end{algorithm}
```
This is implemented with a [[Priority queue]] and it's complete, optimal and has a space and temporal complexity of $O(b^{d+1})$ nodes.

This algorithm can also be implemented with the best first search where the function is the path-cost.
#### Uniform-Cost Search

It generalizes BFS sorting the nodes in the frontier according to their increasing path cost from the root. It does not choose the shallowest node. This algorithm is complete, optimal and it's complexity is $O(b^{1+\lceil C^{*} / \epsilon\rceil})$ nodes. This algorithm is also called [[Dijkstra algorithm]].
#### Depth First Search

It's an algorithm that selects a root node, then, it expands one of its successor the one of its successor, and so on. When it reaches a node without successor, it 'backtracks' and chooses one of the deepest nodes not yet chosen. It's frontier can be represented by a Last-In-First-Out queue (LIFO) or it can be implemented using recursion. A maximum depth can also be set and that is called **depth-limited search**.

It's time complexity is $O(b^{m})$ and spatial complexity is $O(bm)$.

A variant of this is called **backtracking-search** and it uses even less memory than before because it only expands one successor at a time, thus reducing the memory footprint of the algorithm.
#### Iterative deepening search

IDA works by trying different values for $l$ until, either a solution is found, or the depth-limited search returns a failure. This is very similar to the [[Uninformed search strategies#Breadth-First Search]] but rather than saving all the nodes in memory, it just recomputes everything. This may seem too wasteful but in reality since the check is applied multiple times on the top levels, it's not that bad. 
#### Bidirectional search

This approach works by simultaneously searching both forwards and backwards, hoping that the two searches will meet. The motivation is that $b^{d/2} + b^{d/2}$ is much less than $b^{d}$. For this to work the algorithm needs to keep track of the two frontiers and the two tables of reached states.
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{BiSearch}{$problemA, fA, problemB, fB$}
	\State $nodeA \gets NODE(problemA.INITIAL)$
	\State $nodeB \gets NODE(problemB.INITIAL)$
	\State $frontierA \gets$ priority queue ordered by $fA$ with $nodeA$ as element	
	\State $frontierB \gets$ priority queue ordered by $fB$ with $nodeB$ as element
	\State $reachedA \gets$ lookup table with one key $nodeA.STATE$ and value $nodeA$
	\State $reachedB \gets$ lookup table with one key $nodeB.STATE$ and value $nodeB$ 
	\State $solution \gets failure$
	\While{\Not $Teminated(solution, frontierA, frontierB)$}
		\If{$fA(Top(frontierA)) < fB(Top(frontierB))$}
			\State $solution \gets Proceed(A, problemA, frontierA, reachedA, reachedB, solution)$
		\else
			\State $solution \gets Proceed(B, problemB, frontierB, reachedB, reachedA, solution)$
		\EndIf
	\EndWhile
	\Return solution
\EndProcedure
\end{algorithmic}\end{algorithm}
```
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{Proceed}{$dir, problem, frontier, reached1, reached2, solution$}
	\State $node \gets Pop(frontier)$
	\For{$child$ in $Expand(problem, node$}
		\State $s \gets child.STATE$
		\If{$s$ \not in $reached \lor PATHCOST(child) < PATHCOST(reached[s])$}
			\State $reached[s] \gets child$
			\State add $child$ to $frontier$
			\If{$s$ in $reached2$}
				\State $solution2 \gets JOINNODES(dir, child, reached2[s]$)
				\If{$PATHCOST(solution2)<PATHCOST(solution)$}
					\State $solution \gets solution2$
				\EndIf
			\EndIf
		\EndIf
	\EndFor	
\EndProcedure
\end{algorithmic}\end{algorithm}
```
