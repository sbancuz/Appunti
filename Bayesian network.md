---
tags:
  - artificial_intelligence
---
A Bayesian network is a [[Graphs#Directed graphs]] in which each node is annotated with quantitative probability information. 
- each node corresponds to a [[Probability theory#Random variables]]
- a link between node $X$ and node $Y$ is a **parent** relationship and represent a causal relationship
- each node $X_{i}$ has probability information $\theta(X_{i}|\text{Parents}(x_{i}))$ that quantifies the parents effect on the node

To construct a network we can use specific domain knowledge and just assign probability to the nodes, and the topology of the graph will take care of the rest. The local probability information attached to each node is called a **conditional probability table**.

![[LPT.png]]

Bayes nets defines each entry in the joint distribution as
$$
P(x_{1},\dots,x_{n}) = \prod \theta(x_{i} | \text{parents}(x_{i}))
$$
Since **each node is conditionally independent of its other predecessors**, a bayes network is be a complete and non redundant and can also be a more compact representation than a full joint distribution. This is the very reason why specifying a correct topological order is important.

Another important property is that a that a variable is conditionally independent of all other nodes in the network, given its parents, children and children's parents -- it's **Markov blanket**.
### Independence between sets

The most general conditional independence is: given a Bayes net, is a set of nodes $X$ conditionally independent of another set $Y$, given a third set $Z$. This can be efficiently answered by checking if there is $Z$ **d-separation** between $X$ and $Y$. To check this:
1) consider the ancestral subgraph consisting of $X,Y,Z$ and their ancestors
2) add links between any unlinked pair of nodes that share a common child -- this is a **moral graph**
3) replace all directed links by undirected ones
4) check if $Z$ blocks all paths between $X$ and $Y$ in the resulting graph
### Inference 

The basic task for any probabilistic inference system is to compute the posterior probability distribution for a set of **query variables**, given some **event**. Basically we want to compute
$$
Y  = P (X|e)
$$
This can be computed with **probabilistic inference**. To do this we use the full joint distribution as the knowledge base. One common task is to extract the distribution over some subset of variables. This can give the [[Marginal probability]] of some variable.
