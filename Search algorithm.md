---
tags:
  - AI
---
Search algorithms are used to resolve search problems and are implemented to have three states:
- Problem formulation
- Solution searching
- Executing solution

This are most effective for finding good solution on games like tic-tac-toe or chess (disregarding the computational complexity in the last example) and are typical of agents that are fully observable, static, discrete and deterministic.

We use games to develop these algorithms because are complex enough to not just 'brute force' and are easily scalable.

### The 8/15 puzzle

We define a state as a feasible configuration of the 8 tiles on the $3\times 3$ grid and the solution is represented by a sequence of states in the state space.

![[8puzzle.png]]

To solve search problems we have to define some functions:
- action(s) : a function that given the state s returns a set of feasible functions
- result(s, a) : given both a state and an action it returns the resulting state
- cost(s,a,s') : the step cost of an action from s to s'

![[step cost.png]]

An optimal solution is a solution with the lowest cost. The cost of a path is the sum of the costs of the arcs that compose the path.

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
The frontier is implemented as a [[Priority queue]]
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


