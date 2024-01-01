---
tags:
  - artificial_intelligence
---
A Bayesian network is a [[Graphs#Directed graphs]] in which each node is annotated with quantitative probability information. 
- each node corresponds to a [[Probability theory#Random variables]]
- a link between node $X$ and node $Y$ is a **parent** relationship, $X$ is parent of $Y$
- each node $X_{i}$ has probability information $\theta(X_{i}|\text{Parents}(x_{i}))$ that quantifies the parents effect on the node

To construct a network we can use specific domain knowledge and just assign probability to the nodes, and the topology of the graph will take care of the rest. The local probability information attached to each node is called a **conditional probability table**.

![[LPT.png]]

Bayes nets defines each entry in the joint distribution as
$$
P(x_{1},\dots,x_{n}) = \prod \theta(x_{i} | \text{parents}(x_{i}))
$$
