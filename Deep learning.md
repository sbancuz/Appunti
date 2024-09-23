---
tags:
---
Deep learning is the branch of [[Artificial intelligence]] that was born with the goal to replicate how the human brain computes information. 
**Mettere la differenza con sup learning**
We can see the brain as a computer that has an enormous amount of computational units that work all in parallel. This computational model has to also be
- Distributed
- Redundant and fault tolerant
- Parallel

The computational model that we came up is to model the neuron like a [[Perceptron]] -- i.e. like a non-linear function that takes as input many outputs of other neurons and either gets activated or not.
### Hebbian learning

Once we have modeled the brain as a network of [[Perceptron]] we still have the problem of finding the correct weight that exhibit the wanted behavior. Once again we take inspiration from biology and **Hebbian learning** that says that *the strength of a synapse increases according to the simultaneous activation of the relative input and the desired output.*  This can be modeled mathematically as such
$$
w_{i}^{k + 1} = w_{i} ^{k} + \Delta w_{i}^{k} \qquad \Delta w_{i}^{k} = \eta x_{i}^{k}t^{k}
$$
Where we have $\eta$ the **learning rate**, $x_{i}^{k}$ the $i$-th perceptron input at time $k$ and $t^{k}$ the expected output. This is a form of [[Competitive analysis|online]] learning.
### Multi-layer perception

There is a problem, a single [[Perceptron]] can't possibly model complex behaviors, it's just a linear separation boundary in the hypotheses space.  The solution is to make a net