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

Another optimization could be to consider a table of already visited states and their computed value, we call this a **transposition table**. This means that every state will only be evaluated once.
### Alpha-beta pruning

To fix the exponential growth of the states of the game, we can cut the number of spaces to search by about a half.
The general principle is this: consider a node $n$ somewhere in the tree, such that Player has a choice of moving 
to $n$. If Player has a better choice either at the same level or at any point higher up in the tree, then we can stop the search in the branch. This is implemented by modifying the max/min value function to be $\text{MaxValue}(game, state, \alpha, \beta)$ that describe bounds on the backed up values:
- $\alpha \to$ the value of the best path for max -- think of $\alpha$ as **at-least**
- $\beta \to$ the value of the best path for min -- think of $\beta$ as **at-most**

>[!important]
>The order of evaluation matters a lot when using alpha beta pruning 
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
			\State $\beta \gets $ Min($a, v$)
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
### Heuristic alpha beta pruning

To maximize the computation time, we can cut off the search early and apply a heuristic evaluation function. One example of when to use this approach would be chess -- that even with all other optimizations remains to large to check completely. In other words we change:
- $\text{Utility} \to \text{Eval}$
- $\text{Terminal}\to \text{Cutoff}$

The **eval** function returns an **estimate** of the expected utility of state $s$ to $p$ and for terminal states it must be equal to the utility. 
$$
\text{Utility}(loss,p) \leq \text{Eval}(s,p) \leq \text{Utility}(win, p)
$$
Most evaluation functions will work by calculating various **features** -- like in chess the type of remaining pieces. These features taken together will form **categories**. The evaluation function does not know which states are which, but it can return a value that estimates the **proportion** of states with each outcome. 
$$
\text{Eval}(s) = \sum w_{i}f_{i}(s) \qquad \text{ with} \sum w_{i} = 1
$$
Cutting off the search at a fixed depth can easily lead to errors due to the approximate nature of the evaluation function.  For example when reaching a certain $d$ we find a very good move but the opponent response will capture a queen with no compensation. This means that we shouldn't always use the evaluation function, but be restricted to the **quiescent** cases -- that is states where the next action will wildly swing the eval. For the other cases the evaluation function should never be computed.

Another problem would be the **horizon effect** -- that is when an evaluation function will delay an inevitable bad move by doing some other bad moves, ending up in a worse position overall. This can be mitigated by allowing **singular extensions** of some branches of the computation for moves that are *clearly better*.
### Forward pruning
 
Another approach to reduce the search tree is to eliminate *a priori*  some really bad moves to focus the search on the other moves. This is akin on how a human would play a game of chess, by discarding the obvious bad moves and focusing on the few good moves in the position.

This approach obviously poses some risks because it could miss a good move after a *obviously bad* one, thus ending up in a worse position because it didn't check that tree. Another idea would be to do **late move reduction** that checks this bad states, but with a lesser depth than the other branches.
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