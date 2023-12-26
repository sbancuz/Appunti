---
tags:
  - operations_research
---
If the augmenting path is not appropriately chosen, pathological cases may take place, causing a huge increase in the number of iterations being necessary to determine the optimal solution. 

![[pathological flow.png]]

This example clearly shows that the maximum flow is $2000$, the problem is if the augmenting path algorithm considers the arcs $(1,2), (2,1)$, then the number of iterations goes from $2$ to $2000$. The Edmonds-Karp ensures a polynomial [[Complexity of an algorithm]]. The only trick adopted in this algorithm is to use the [[Search problem#Breadth-First Search]] and then augmenting the algorithm with the least number of arcs in the path. The resulting complexity is $(m^{2}n)$