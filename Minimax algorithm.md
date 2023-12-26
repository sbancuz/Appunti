---
tags:
  - artificial_intelligence
---
This algorithm is used to find the optimal strategy for resolving a specific [[Adversarial search strategies]] problem. This is done by working out the **minimax value** -- its utility value -- of each state in the tree.

The utility is $> 0$ if max is winning, $= 0$ when there is a tie and $<0$ if min is winning.

![[minimax.png]]

In these kind of problems max will always try to find the maximum state value and min the minimum one. So
$$
\text{Minimax}(s) = \begin{cases}
\text{Utility}(s, max) & \text{Is-Terminal}(s) \\
\max_{a \in \text{Actions}(s)} \text{Minimax}(\text{Result}(s,a)) & \text{To-move}(s) = max \\
\min_{a \in \text{Actions}(s)} \text{Minimax}(\text{Result}(s,a)) & \text{To-move}(s) = min  
\end{cases}
$$
>[!note]
>This definition assumes optimal play for min

```pseudo
\begin{algorithm}\begin{algorithmic}
\procedure{Minimax-Search}{$game, state$}
	\State player $\gets$ game.ToMove($state$)
	\State value, move $\gets$ MaxValue($game, state$) 
	\Return $move$
\EndProcedure
\end{algorithmic}\end{algorithm}
\begin{algorithm}\begin{algorithmic}
\procedure{Max-value}{$game, state$}
	\If{$game$.IsTerminal($state$)}
		\Return $game$.Utility($state, player$), $null$
	\EndIf
	\State $v, move \gets - \infty$
	\For{$a$ in $game$.Actions($state$)}
		\State $v2, a2 \gets $ MinValue($game, game$.Result(state, a))
		\If{$v2 < v$}
			\State $v, move \gets v2, a$
		\EndIf 
	\EndFor
	\Return $v, move$
\EndProcedure
\end{algorithmic}\end{algorithm}
\begin{algorithm}\begin{algorithmic}
\procedure{Min-value}{$game, state$}
	\If{$game$.IsTerminal($state$)}
		\Return $game$.Utility($state, player$), $null$
	\EndIf
	\State $v, move \gets + \infty$
	\For{$a$ in $game$.Actions($state$)}
		\State $v2, a2 \gets $ MaxValue($game, game$.Result(state, a))
		\If{$v2 < v$}
			\State $v, move \gets v2, a$
		\EndIf 
	\EndFor
	\Return $v, move$
\EndProcedure
\end{algorithmic}\end{algorithm}
```
This algorithm is optimal when it can search the whole tree, but not when it's limited to using an evaluation function.

The minimax algorithm performs a complete [[Uninformed search strategies#Depth First Search]] of the game tree, this means that its complexity is $O(b^{m})$ and the space complexity is $O(bm)$. This makes it impractical for complex games like chess, because its branching factor is 35 and the average game has a depth of about 80 ply.
### Alpha-beta pruning

To fix the exponential growth of the states of the game, we can cut the number of spaces to search by about a half.
The general principle is this: consider a node $n$ somewhere in the tree, such that Player has a choice of moving 
to $n$. If Player has a better choice either at the same level or at any point higher up in the tree, then we can stop the search in the branch. This is implemented by modifying the max/min value function to be $\text{MaxValue}(game, state, \alpha, \beta)$ that describe bounds on the backed up values:
- $\alpha \to$ the value of the best path for max -- think of $\alpha$ as **at-least**
- $\beta \to$ the value of the best path for min -- think of $\beta$ as **at-most**

```pseudo
\begin{algorithm}\begin{algorithmic}
\procedure{Alpha-Beta-Search}{$game, state$}
	\State player $\gets$ game.ToMove($state$)
	\State value, move $\gets$ MaxValue($game, state, -\infty, \infty$) 
	\Return $move$
\EndProcedure
\end{algorithmic}\end{algorithm}
\begin{algorithm}\begin{algorithmic}
\procedure{Max-value}{$game, state, \alpha, \beta$}
	\If{$game$.IsTerminal($state$)}
		\Return $game$.Utility($state, player$), $null$
	\EndIf
	\State $v, move \gets - \infty$
	\For{$a$ in $game$.Actions($state$)}
		\State $v2, a2 \gets $ MinValue($game, game$.Result($state, a$), $\alpha, \beta$)
		\If{$v2 < v$}
			\State $v, move \gets v2, a$
			\State $\alpha \gets $ Max($a, v$)
		\EndIf 
		\If{$v \ge \beta$}
			\Return $v, move$
		\EndIf
	\EndFor
	\Return $v, move$
\EndProcedure
\end{algorithmic}\end{algorithm}
\begin{algorithm}\begin{algorithmic}
\procedure{Min-value}{$game, state$}
	\If{$game$.IsTerminal($state$)}
		\Return $game$.Utility($state, player$), $null$
	\EndIf
	\State $v, move \gets + \infty$
	\For{$a$ in $game$.Actions($state$)}
		\State $v2, a2 \gets $ MaxValue($game, game$.Result($state, a$), $\alpha, \beta$)
		\If{$v2 < v$}
			\State $v, move \gets v2, a$
			\State $\alpha \gets $ Min($a, v$)
		\EndIf 
		\If{$v \le \alpha$}
			\Return $v, move$
		\EndIf
	\EndFor
	\Return $v, move$
\EndProcedure
\end{algorithmic}\end{algorithm}
```
If this could be perfectly done it would bring down the [[Complexity of an algorithm]] to $O(b^{m/2})$. This means that the branching factor becomes $\sqrt{ b }$.
### Expectiminimax

This is a variation meant to represent stochastic searches. To be able to represent the uncertainty of the outcome of the moves we introduce **chance nodes** -- one for each possible outcome -- and put them after every decision. Since positions do not have definite minimax values, we can only calculate the **expected value** of a position using the average of the scores.
$$
\text{EMinimax}(s) = \begin{cases}
\text{Utility}(s, max) & \text{Is-Terminal}(s) \\
\max_{a \in \text{Actions}(s)} \text{EMinimax}(\text{Result}(s,a)) & \text{To-move}(s) = max \\
\min_{a \in \text{Actions}(s)} \text{EMinimax}(\text{Result}(s,a)) & \text{To-move}(s) = min \\
\sum_{r}P(r) \text{EMinimax(Result(s,r))}  & \text{To-move}(s) = chance
\end{cases}
$$
If the evaluation is bounded, then we can optimize the search using alpha-beta pruning.