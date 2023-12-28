---
tags:
  - artificial_intelligence
---
A CSP search algorithm takes advantage of the structure of the states to create a **general** heuristic to enable the solution of complex problems. The main idea is to eliminate large portions of the search space all at once by identifying variable/value combinations that violate some [[Model optimization problems#Constraints]].

Exploiting the structure of the states means that I can modify the branching factor depending on the action that -- by looking at the failures as soon as possible -- I'm taking, thus greatly diminishing the search space and improving performance.

Each CSP has:
- A set $X$ of variables with associated set of $D$ domains
- A set of $C$ constraints that involves a subset of variables and specifies combinations of their values.

A solution can be **complete** if all variables are assigned a value and **consistent** if all the constraints are satisfied.
### CSP as a [[Search problem]]

To define a CSP as a search problem we can represent:
- States $\to$ empty assignments with $k=0$
- $\text{Actions}(\{ X_{i1} \gets v_{i 1}, X_{i_{2}} \gets v_{i 2}, \dots, X_{ik} \gets v_{i k}\}) \to$ all possible consistent assignments for $X_{ik+1}$
- $\text{Result}(\{ \dots \}) = \{ X_{i1} \gets v_{i 1}, X_{i_{2}} \gets v_{i 2}, \dots, X_{ik} \gets v_{i k}, X_{ik + 1} \gets v_{i k + 1}\}$
- Goal test $\to k= n$ 

>[!tip]
>The step cost is considered unitary
#### Commutativity

The order in which values are assigned to the variables has no impact on the possibility of reaching consistent and complete assignments, but it does impact the performance of the search.

A consequence of the commutativity is that the branching factor greatly diminishes because we can ignore all the variables $X$ that are associated to $N$ -- this means that we don't have to repeat decisions. 

Another consequence is that the path has always length $k$, this means that the path doesn't matter to the cost and, thus, all the solutions are optimal. To get this solution we can just use [[Uninformed search strategies#Depth First Search]] and just backtrack.