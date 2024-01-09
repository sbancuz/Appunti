---
tags:
  - databases
---
In business applications most queries have an exact result, this result may be sorted in regard to some metric, but there is no concept of **preference**. But some application do require raking results based on some criterion.

This becomes an [[Model optimization problems]] with the form of 
$$
\text{Given } N \text{ objects described by } d \text{ attributes, find the best } k \text{ objects}
$$
This technique is very relevant in search engines, recommender systems and even [[machine learning]].
### Rank aggregation

This is the problem of combining results of several ranked lists of objects in a way to produce a single consensus ranking.

There were the first 2 approaches:
- Borda's $\to$ the winner is the candidate with the least penalty
- Condorcet $\to$ it counts how many times $a$ beats $b$ and ranks them

But these presented some problems, like for the Condorcet's method there could be cyclical winners. After that the new approach was the metric one defined as the problem of finding a new ranking $R$ whose total distance to the initial ranking $R_{1},\dots,R_{n}$ is minimized. Several ways to define distance were developed:
- Kendall tau $\to$ $K(R_{1},R_{2})$ is defined as the number of swaps when using bubble sort
- Spearman's footrule $\to$ $F(R_{1},R_{2})$ is defined as the sum of the distance between the ranks of the same item in two rankings

There are other techniques that use only the position of the elements in the raking denoted as **opaque ranking**.
One such example is the **MedRank** that is based on the notion of a median and provides an approximation of the footrule aggregation.
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{MedRank}{$k, Rlist$}
	\State use sorted accesses in each list, until there are $k$ elements that occur in more than $m/2$ lists
		\State These are the top $k$ elements
\EndProcedure
\end{algorithmic}\end{algorithm}
```
>[!example]-
>![[medrank.png]]
### Top k queries

The aim is to retrieve only the $k$ best answers from a potentially large result set. The naive approach is to assume a **scoring function** $S$ that assigns to each tuple $t$ a numerical score for ranking tuples. 

For this we have to make a couple of assumptions:
- **sorted access** $\to$ each access returns the id of the next best object and its score
- **random access** $\to$ requires an index on the primary key
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{NaiveTopK}{$R$}
	\For{$t \in R$}
		\State compute $S(t)$ 
	\EndFor 
	\State sort tuples based on the score
	\Return the best first $k$ highest tuples
\EndProcedure
\end{algorithmic}\end{algorithm}
```
But this approach is to expensive for large datasets because it requires sorting and it's even worse if more than one relation is involved.

Another approach is to order the semantics of the top-k queries. With this only the first $k$ tuples becomes part of the result. The problem is that this approach is non-deterministic.

The most common scoring functions are:
- Sum
- Avg
- Min
- Max

Rather than scoring we can use a **distance function** and get the k-nearest neighbors. For distances we can consider the Lp distance function
$$
L_{p}(t,q) = \left( \sum|t_{i}-q_{i}|^{p} \right)^{1/p}
$$
If we consider also the weights we get
$$
L_{p}(t,q,W) = \left( \sum w_{i} | t_{i} - q_{i}|^{p} \right)^{1/p}
$$
 
### Skyline queries