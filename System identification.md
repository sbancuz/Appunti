---
tags:
  - mida
---
[[System]] Identification is the discipline that studies the methodologies to derive a model from data
```math
||{"id":1413641698919}||


```
What do we expect of this model:
- Limited validity $\to$ this model won't be general since it's given by just data
- The physical interpretation is difficult to understand
- Simpler to derive and to use

>[!warning] Assumptions
>- Model class selection (linear? [[ARMAX process]]? ..., order?)
>- Real data contains noise or other sources of imperfections
>- The process may vary over time, this could make our model only valid locally
>- Some signals or variables are not always measurable

We can define the system $\mathcal S$, the model family $\mathcal M$, the identification method $\mathcal I$ and, lastly, the identification experiment $\mathcal E$  
### Phases

1) Experiment design and data collection
	First things first, one must design and preform and **identification experiment** to obtain the data. So we need to chose the kind of input to feed to the system and the choice of the data length $N$. After we need to sanitize the data. Another worry is whether or not there is a feedback from the output to the input, or there could be constraints on the system.

2) Choice of the model class
	The identification problem consists in the determination of the appropriate parametrization:
	- static/dynamic
	- discrete/continuous
	- linear/non-linear
	- time-invariant/time-variant
	- non-parametric models

3) The identification method
	This is an [[Model optimization problems]] that tries to minimize the error. This could be trivial for some classes of models like the [[Autoregressive process]].

4) Model validation
	This is a quality check on the obtained model to check if it fits the criteria and actually represents the original phenomenon. If this doesn't pass it's back to the drawing board to redo 1) 2) or 3)
### Static modeling

The general identification problem setting assumes that one has observed some input/output data from a system and looks for a model that can explain the relationship between them. To start off the focus on **static models** between 2 variables
$$
\hat{y}(t) = f(u(t); \theta)
$$
where 
- $t$ is an index that univocally defines the in/out pair
- $\theta$ is the vector of model parameters
- $y(t)$ only depends on $u(t)$ at the same index $t$

This procedure starts from a conjecture about the type of relationship, then we find the **best** model by using a **fitting** technique. This is usually dome by the [[Minimizing least squares]].

A natural way to describe $f(u; \theta)$ is using a functional expansion
$$
f(u; \theta) = \phi^{T}\theta = \sum\theta\phi(u) \qquad \phi(u) \text{ is a basis function}
$$
and once we have defined a family of functions parameterized by a vector $\theta$, we have to search the parametrization that yields the best **approximation** of $y(t)$ over the available data.

>[!note] 
>A model is **identifiable** when there is only one solution for the regression.
### Dynamical modeling

The identification of dynamical models presents some additional difficulties and pitfalls:
- The identification algorithm $\mathcal I$ depends on the considered model class
- The role of the noise model is crucial
- It's not so simple to define idenfiability

