---
tags:
  - artificial_intelligence
---
With adversarial search it's intended the search in which our agent will explore and compete in an environment where other [[Rational Agents]] are plotting against us.

There are at least three stances we can take towards multi agent [[Rational Agents#Environment]]:
- Aggregate them all in an **economy**
- Consider other adversarial agents as just a part of the environment that makes it non deterministic
- Explicitly model the adversarial agents with the techniques of adversarial game tree search
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

The objective of max is to find a sequence of moves that will lead to a win, but so is the objective of min. This means that both of their strategies must be a conditional path -- a contingent strategy specifying a response to min's moves. To find this path we can use the Minimax algorithm.

![[Minimax algorithm]]
>[!tip]
>This approach can be generalized for multiplayer games by representing not only the two values, but a vector containing all the values of the agents


