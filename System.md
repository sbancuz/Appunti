---
tags:
  - mida
---
System Identification is the discipline that studies the methodologies to derive a model from data
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
### Static systems

A system from which the **input** is sufficient to predict the **output**. [[Machine learning]] deals with this exact problems.

>[!example]-
>![[static sys exa.png]]

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
### Dynamic systems

In dynamic systems the output will depend from both the **input** and the **time**. Time description can be either **continuous** or **discrete**.
This type of problem can also be called a **regression** problem.

>[!example]-
>![[dynamic sys exa.png]]

When dealing with time we have to differentiate the 2 cases in order to model the problem:
- Continuous $\to$ [[Equazioni differenziali ordinarie|EDO]]
- Discrete $\to$ [[Difference equation]]

When dealing with discrete functions is clear that the $y(t)$ depends on its past values. We still wish to learn a function $f$, so that $y(t) = f(\phi(t))$ but now $\phi(t)$ may contain past samples of both inputs and outputs.

The identification of dynamical models presents some additional difficulties and pitfalls:
- The identification algorithm $\mathcal I$ depends on the considered model class
- The role of the noise model is crucial
- It's not so simple to define idenfiability
### Model families

We can also distinguish $2$ different types of data generating mechanisms, depending on the presence of **exogenous variables**:
- Time series
	We are given a set of observation of a variable over some time and we need to build a model that describes it's evolution
$$
v(t) = W(z)\eta(t), \qquad \eta(t) \sim\text{Wn}(0,\lambda^{2})
$$
- Input-output system
	We are given a set of observation of both the input and the output of a given system over some time, and we want to know how the input influences the output
$$
y(t) = G(z) u(t-k) + W(z)\eta(t), \qquad \eta(t)\sim \text{Wn}(0,\lambda^{2})
$$
### Disturbance models

Another classification we can have is based on the disturbance model:
- [[Output error models]]
- Equation error models or [[Autoregressive process]]
- [[ARMA process]]/[[ARMAX process]]
- [[ARXAR model]] 
- [[ARIMA or ARIMAX models]]
- [[FIR models]] 
### Selection of the model

When modeling a problem, we need to make 2 decisions: the model family and the model structure. To make this decision there are a couple of key factors:
- Purpose
- Flexibility in terms of a sufficient number of degrees of freedom
- Parsimony, i.e. the simpler the better
- Algorithm complexity
- Performance index

>[!warning]
Solutions are not always **unique**. 

Assume that the true system falls exactly in the considered model class $\mathcal S \in \mathcal M(\theta)$
$$
\mathcal S: y(t) = G_{0}(z) u(t-k) + W_{0}(z)\eta_{0}(t), \qquad \eta_{0}(t) \sim \text{Wn}(0,\lambda_{0}^{2})
$$
Even so, it's not granted that the identification is successful. Let $\mathcal D(\mathcal S,\mathcal M)$ be the set of parameterizations for which $\mathcal M(\theta)$ provides a perfect description of $\mathcal S$. $3$ things can occur
- $\mathcal D(\mathcal S,\mathcal M) = \emptyset$ $\to$ under parameterized model
- $\mathcal D(\mathcal S,\mathcal M) = \{ \theta_{0} \}$ $\to$ single point and ideal case
- $\mathcal D(\mathcal S,\mathcal M) = \{ \theta_{0},\theta_{1},\dots \}$ $\to$ multiple points and overparameterized

Once the model family has been selected and some $N$ data has been collected. How can we select the best $\theta$, i.e. the model, that best interprets the data. We can say that a model is **good** if it provides an accurate $1$-step ahead predictions
$$
\mathcal  M (\theta) \to \hat{\mathcal M}(\theta): \begin{cases}
\hat{y}(t+1|t) = f(y(t)), y(t-1), \dots:\theta) & \text{For time series} \\
\hat{y}(t+1|t) = f(u(t), u(t-1), \dots, y(t), y(t-1), \dots:\theta) & \text{For I/O systems}
\end{cases}
$$
and the error to minimize is given by 
$$
\epsilon(t;\theta) = y(t) -\hat{y}(t|t-1;\theta)
$$
and average size of the error
$$
J_{N}(\theta) = \frac{1}{N}\sum_{\tau}^{N}\epsilon(t;\theta)^{2}
$$
where $\tau$ is the lowest integer where $\epsilon(t)$ can be computed. However this is still not enough, we have to check that the error is a [[White noise]], only then we can say that the model is optimal.

The [[Prediction]] form model is used to get the optimal model by constructing the error.

![[prediction form mdoel.png]]

Say we select the model $\theta$ from $\mathcal M$
$$
\mathcal M(\theta) : y(t) = G(z)u(t-k) + W(z)\eta(t)
$$
Now, only if the zeros are not on the unit circle, we can get the whitening filter
$$
y(t) = \left( 1-\frac{1}{W(z)} \right)y(t) + \frac{G(z)}{W(z)}u(t-k) + \eta(t)
$$
Now since $W(z)$ is a ration of a monic, it implies that the RHS depends on $y()$ up to $t-1$, so they are uncorrelated to the noise. This means that
$$
\hat{\mathcal M} : \hat{y}(t|t-1) =\left( 1-\frac{1}{W(z)} \right)y(t) + \frac{G(z)}{W(z)}u(t-k) 
$$
