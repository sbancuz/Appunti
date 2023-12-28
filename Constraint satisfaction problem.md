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
### Inference 

A way to speed up the computation of the CSP is to reduce the domain of the legal values for a variable, this is done by **constraint propagation**, i.e. the act of using the constraints of a problem to reduce the legal values of variables. This can be implemented at any time during the computation or even at the preprocessor stage.

The key idea is **local consistency**, if we treat each variable as a node in a graph and each binary constraint as an edge, then the process of enforcing local consistency in each part of the graph causes inconsistent values to be eliminated.
#### Node consistency

A single variable is **node-consistent** if all the values in it's domain satisfy the variable's constraints. This is very easy to do an most algorithm take this as a given.
#### Arc consistency

A variable is **arc-consistent** if every value in its domain satisfies the variable's binary constraints. More formally $X_{i}$ is arc consistent to $X_{j}$ iff for every value in $D_{i}, D_{j}$ satisfies a constraint on the arc $(X_{i},X_{j})$. To make every variable arc-consistent we can use the AC-3 algorithm.

```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{AC3}{$csp$}
	\State $ queue \gets $ all of the csp arcs in a queue
	\While{$queue$ is not empty}
		\State $(X_i, X_j) \gets $ Pop($queue$)
		\If{Revise($csp, X_i, X_j$)}
			\If{SizeOf($D_i$) = 0}
				\Return \False
			\EndIf
			\For{each $X_k$ in $X_i.$NEIGHBORS - $\{X_j\}$}
				\State add ($X_k, X_i$) to queue
			\EndFor
		\EndIf
	\EndWhile
	\Return \True
\EndProcedure
\end{algorithmic}\end{algorithm}
\begin{algorithm}\begin{algorithmic}
\Procedure{Revise}{$csp, X_i, X_j$}
	\State $revised \gets false$
	\For{ each $x$ in $D_i$}
		\If{no $y \in D_j$ allows $(x, y)$ to satisfy the constraints}
			\State $D_i$.delete($x$)
			\State $revised \gets true$
		\EndIf
	\EndFor
	\Return $revised$
\EndProcedure
\end{algorithmic}\end{algorithm}
```
#### Path consistency

**Path-consistency** reduces the binary constraints by using implicit constraints that are inferred by looking at triples of variables. A set $\{ X_{i},X_{j} \}$ is path-consistent to $X_{m}$ iff for every consistent assignment $\{ X_{i} = a,X_{j} =b \}$ there is an assignment to $X_{m}$ that satisfies $\{ X_{i}, X_{m} \}$ and $\{ X_{m}, X_{j} \}$. This can be generalized to $k$-consistency by adding more intermediate values.
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
#### Variable and value ordering

We still haven't answered **how** should the next values be chosen and in what order. The simplest strategy would be to do static ordering, i.e. go in the order the values are given, or random ordering. Neither strategy is optimal.

The next idea is to use the **minimum-remaining-values** heuristic and it selects the variable that has the fewest *legal* values. This usually speeds up the computation by orders of magnitude, but isn't a silver bullet. In the cases that we need to check states that have the same number of values we can use the **degree heuristic** -- tries to reduce the branching factor on future choices by selecting the variable that is involved in the largest number of constraints on other unassigned variables.
#### Search and inference

We can inference a lot of information during the course of a search, by making new choices we can reduce the domain on the neighboring values. The simplest form of this is called **forward checking**. Whenever a variable $X$ is assigned we can establish arc consistency for it, and thus can apply AC-3.