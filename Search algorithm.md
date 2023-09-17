---
tags:
  - AI
---
Search algorithms are used to resolve search problems and are implemented to have three states:
- Problem formulation
- Solution searching
- Executing solution

This are most effective for finding good solution on games like tic-tac-toe or chess. (disregarding the computational complexity in the last example)

We use games to develop these algorithms because are complex enough to not just 'brute force'.

### The 8/15 puzzle

We define a state as a feasible configuration of the 8 tiles on the $3\times 3$ grid and the solution is represented by a sequence of states in the state space.

![[8puzzle.png]]

The first things to define are the actions that i can do while in a specific state. In this case an action can be represented by the movement of the blank space.