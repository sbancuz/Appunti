---
tags:
  - artificial_intelligence
---
Search algorithms are used to resolve search problems in a known environment are implemented to have three states:
- Problem formulation
- Solution searching
- Executing solution

>[!warning]
>It's important for the environment to be known, fully observable and deterministic

This approach for finding a solution is called **open-loop** because the [[Rational Agents]] can ignore its percepts and still arrive at the solution, if the environment was non-deterministic a **closed-loop** solution would've been better.

This are most effective for finding good solution on games like tic-tac-toe or chess (disregarding the computational complexity in the last example) and are typical of agents that are fully observable, static, discrete and deterministic.

We use games to develop these algorithms because are complex enough to not just 'brute force' and are easily scalable.
### The 8/15 puzzle

We define a state as a feasible configuration of the 8 tiles on the $3\times 3$ grid and the solution is represented by a sequence of states in the state space and that can be achieved with [[Graphs]].

![[8puzzle.png]]

To solve search problems we have to define some functions:
- action(s) : a function that given the state s returns a set of feasible functions
- result(s, a) : given both a state and an action it returns the resulting state
- cost(s,a,s') : the step cost of an action from s to s'

![[step cost.png]]

An optimal solution is a solution with the lowest cost. The cost of a [[Paths]] is the sum of the costs of the arcs that compose the path.

The problem arises with the size of the state space, because it tends to be massive. For example the 8-puzzle has $9! = 362880$ states, and the 15-puzzle $16!$ which is computationally taxing just for a relatively small and simple game.
## Reducing the search space

A problem can have different search spaces depending by the interpretation that has been given to it.
The solutions are found by building a search tree from the state graph.

![[search tree.png]]

If a state has already been visited then the search tree can be infinite even if the states space is finite.
```pseudo
   \begin{algorithm}
    \begin{algorithmic}
      \PROCEDURE{Simple-tree-search-algorithm}{$root, solution$} 
	    \While{\True}
		    \If{there are no more candidate for expansion}
			    \Return $\textbf{Failure}$
			\EndIf
			\State select a node not yet expanded
			\If{the node corresponds to a goal state}
				\Return $\textbf{Found}$
			\Else
				\State expand the chosen node, adding the resulting nodes to the tree
			\EndIf
	    \EndWhile
      \ENDPROCEDURE
      \end{algorithmic}
    \end{algorithm}
```
The set of unexpandend nodes is called the frontier and it is implemented as a [[Priority queue]].
### The eight-queens puzzle

This puzzle consist in placing 8 queens on a chess board such that none of them attack each other at the same time.
#### First formulation
- States : all arrangements of $0,1,2,\dots,8$ queens on the board $1.8\times 10^{14}$ states
- Initial state : an empty chess board
- Actions : all the possible ways to add one queen in an empty square

These are too many states to check, we need to find a way to minimize the state space, in other words we need to define better what is the state space in the first place.
#### Second formulation
- States : all arrangements of $0,1,2,\dots,8$ queens **in the k leftmost columns with no two queens attacking each other** $2057$ states
- Initial state : an empty chess board
- Actions : all the possible ways to add one queen in an empty square **that is not attacked by any queen already**

>[!Note]
>The problem remained the same, but just changing the search space reduced the complexity so much that before the solution couldn't be found at all, now it's just a matter of milliseconds
>
### Best first search

This is a general approach for expanding the frontier of search [[Graphs]]. 

```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{BestFirstSearch}{$problem, f$}
	\State $node \gets Node(State = problem.INITIAL)$
	\State $frontier \gets $ priority queue ordered by $f$
	\State $reached \gets $ lookup table with one entry with $\{problem.INITIAL, node\}$
	\While{\Not $IsEmpty(frontier)$}
		\State $node \gets Pop(frontier)$
		\If{$problem.IsGoal(node.STATE)$}
			\Return $node$
		\EndIf
		\For{$child$ in $EXPAND(problem, node)$}
			\State $s \gets child.STATE$
			\If{$s$ is not in $reached \lor child.PATHCOST < reached[s].PATHCOST$ }
				\State $reached[s] \gets child$
				\State add $child$ to $frontier$
			\EndIf
		\EndFor
	\EndWhile 
\EndProcedure
\end{algorithmic}\end{algorithm}
```

```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{Expand}{$problem, node$}
	\State $s \gets Node.STATE$
	\For{$action$ in $problem.ACTIONS(s)$}
		\State $s' \gets problem.RESULT(s, action)$
		\State $cost \gets node.PATHCOST + problem.ACTIONCOST(s, action, s')$
		\State \textbf{yield} $NODE(State = s', Parent = node, Action = action, PATHCOST = cost)$
	\EndFor
\EndProcedure
\end{algorithmic}\end{algorithm}
```
### Evaluation of a search algorithm

A search algorithm is evaluated by it's:
- Completeness : is the search strategy guaranteed to find a solution when there is one?
- Optimality :  does the search find the best solution?
- [[Complexity of an algorithm]] : time and space complexity
- Parameters : 
	- $b \to$ is the branching factor
	- $d \to$ is the depth of the shallowest goal node
### Uninformed search strategies

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

A mix of all of the approaches above is the **iterative deepening search**. This works by trying different values for $l$ until, either a solution is found, or the depth-limited search returns a failure. This is very similar to the BFS but rather than saving all the nodes in memory, it just recomputes everything. This may seem too wasteful but in reality since the check is applied multiple times on the top levels, it's not that bad. 
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
### Informed search strategies

Unlike the *normal* search algorithms, informed search strategies use domain specific hints about the location of goals. These hints come in the form of a **heuristic function** denoted $h(n)$.

>[!example]
>In route finding problems, we can estimate the distance from the current state to a goal by computing the straight line distance on the map between the two points.
#### Greedy best-first search

This is a form of best-first search that expands first the node with the lowest $h(n)$ value on the grounds that is likely to lead to a solution quickly. On each iteration it tries to get as close to a goal as it can. Even though it's fast being $O(|V|)$ for the time complexity, it does not guarantee the best solution to the problem. With a good heuristic function , however, the time complexity can be reduced substantially, and on certain problems reaching $O(bm)$
#### A star

The most common informed search algorithm is A start search, a variation of best first search that uses 
$$
f(n) = g(n) + h(n)
$$
where $g(n)$ is the path cost from the initial state to node $n$, and $h(n)$ is the **estimated** cost of the shortest path from $n$ to a goal state. This algorithm is complete, but whether A star is cost optimal or not it depends on certain properties of the heuristic:
- Admissibility -> it never overestimates the cost to reach a goal
- Consistency -> every node $n$, every successor $n'$ generated by an action $a$ has $h(n)\leq c(n,a,n') + h(n')$

A useful way to visualize a search is to draw **contours** in the state space, just like in a topographic map.

![[contour.png]]

It should be clear that as you extend a path, the $g$ cost are **monotonic** -- the path cost always increases as you go along a path, because action costs are always positive. Therefore you get concentric contour lines that don't cross each other. The problem is that is not obvious whether the $f= g + h$ cost will monotonically increase, in fact this property holds only if $h(n) \leq c(n,a,n') + h(n')$.

>[!note]
>A path might contribute several nodes in a row with the same $g + h$ score. This will happen if whenever the decrease in $h$ is exactly equal to the action cost just taken.

If $C^{*}$ is the cost of the optimal solution path, then we can say the following:
- $A^{*}$ expands all nodes that can be reached from the initial state on a path where every node has $f(n) < C^{*}$
- $A^{*}$ might expand some of the nodes right on the goal contour where $f(n) = C^{*}$
- $A^{*}$ doesn't expand any nodes with $f(n) > C^{*}$

With this we can say that $A^{*}$ with a consistent heuristic is **optimally efficient** in the sense that any algorithm that extends search paths from the initial state must expand all nodes that are surely expanded by $A^{*}$. 

$A^{*}$ is very efficient because it **prunes** away search tree nodes that are not necessary for finding an optimal solution.
#### Satisficing search

If we are willing to accept solutions that are suboptimal, but "good enough" -- what we call **satisficing solutions** -- we need to allow $A^{*}$ to use inadmissible heuristic.

>[!example]
>![[weighted a star.png]]

We can call the approach of having weights for every node the **weighted $A^{*}$ search** where we weight the heuristic value more heavily, giving us the evaluation function $f(n) = g(n) + W \times h(n)$ for $W > 1$.

>[!note]
>This could be seen as a greedy search algorithm, because it's not focused on finding a optimal solution