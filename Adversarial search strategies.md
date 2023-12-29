---
tags:
  - artificial_intelligence
---
With adversarial search it's intended the search in which our agent will explore and compete in an environment where other [[Agents]] are plotting against us.

There are at least three stances we can take towards multi agent [[Agents#Environment]]:
- Aggregate them all in an **economy**
- Consider other adversarial agents as just a part of the environment that makes it non deterministic
- Explicitly model the adversarial agents with the techniques of adversarial game tree [[Search problem]]
### Two players zero sum games

The games most commonly studied with AI are what game theorist call deterministic, two player, turn taking, **perfect information, two sum** games. The last two adjectives mean that the game has perfect information and is fully observable.

We define the two players by calling them **max** and **min**. Max will always move first, and then the players will take turns. The turn of each players is called a **ply**. A game can be formally defined with:
- $S_{0}\to$ The initial state
- $\text{To-Move}(s) \to$ The player whose turn it is to move in state $s$
- $\text{Actions}(s) \to$ The set of legal moves is $s$ 
- $\text{Result}(s, a)\to$ The transition model
- $\text{Is-Terminal(s)}\to$ A terminal test which is true when the game is over
- $\text{Utility(s,p)}\to$ An objective function which defines a numerical value on the final move

>[!note]
>The $\text{Actions}$ and $\text{Result}$ function define the state space graph. We can also define the **complete game tree** as a search tree that follows every sequence of moves all the way to a terminal state. This can be used only for small games like tic-tac-toe because of its high memory and computation requirements.

The objective of max is to find a sequence of moves that will lead to a win, but so is the objective of min. This means that both of their strategies must be a conditional path -- a contingent strategy specifying a response to min's moves. To find this path we can use the [[Minimax algorithm]].

>[!tip]
>This approach can be generalized for multiplayer games by representing not only the two values, but a vector containing all the values of the agents
### Monte Carlo tree search

The basic MTCS does not use [[Minimax algorithm#Heuristic alpha beta pruning]], instead the value of a state is estimated as the average utility over a number of **simulations** of complete games from that states.

But how can we choose the moves in the simulations? We need a **playout policy** that biases moves towards the *good ones* by using [[Machine learning]]. Now given we have left to decide:
- from what position do we stater the playouts?
- how many playouts do we allocate at each position?

For some games we can do a **pure Monte Carlo search** by doing $N$ simulation at the starting positions. For some stochastic games this approach works, but for most is not sufficient, we need also a **selection policy** that focuses computational resources on the important parts of the tree balancing exploration and exploitation and is implemented as such:
- Selection $\to$ descends the tree selecting successors using the policy until it finds a new node or a leaf
- Expansion $\to$ if the node is not the goal, it will expand the tree
- Simulation $\to$ simulate the game from the current node
- Backpropagation $\to$ the reward is used to update all the nodes visited during the previous steps
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{MonteCarloTreeSeach}{$state$}
	\State $tree \gets $ Node($state$)
	\While{IsTimeRemaining()}
		\State $leaf \gets $ Select($tree$)
		\State $child \gets $ Expand($leaf$)
		\State $result \gets $ Simulate($child$)
		\State  BackPropagate($result, child$)
	\EndWhile
\EndProcedure
\end{algorithmic}\end{algorithm}
```
One very effective selection policy is called **upper confidence bounds applied to trees**

![[UCB.png]]

### Stochastic search

Stochastic means that we know the probability of each outcome when making a decision. To resolve these types of problems we use a variation of minimax called [[Minimax algorithm#Expectiminimax]].
