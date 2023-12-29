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

This approach for finding a solution is called **open-loop** because the [[Agents]] can ignore its percepts and still arrive at the solution, if the environment was non-deterministic a **closed-loop** solution would've been better.

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
### Search strategies

Depending on the type of problem to resolve, be it winning a chess game or finding the shortest path, we can use:
- [[Uninformed search strategies]]
- [[Informed search strategies]]
- [[Adversarial search strategies]]
### Specialized search strategies

In the problems presented before, the representation of the state is generic and lets us only use it to compare if it is equal to another one. We can lose some generality to improve the search techniques. One such example of this is the [[Constraint satisfaction problem]]. 