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
### Experimental vs Structural identifiability

If it's possible to **unambiguously estimate all parameters** -- $\Delta$ is a singleton -- we say that the system is identifiable. This depends on 
- $\mathcal E$ $\to$ Identification experiment
- $\mathcal M$ $\to$ model family

>[!warning]
>The input should be sufficiently rich of information content to allow the unambiguous estimation of all parameters

In summary
- If $\mathcal E$ can be freely designed, then ensure that all that one need to identify is identifiable
- If not, limit the model family to what's actually identifiable
### Uncertainty of the parameters

Assume $\Delta=\{ \bar{\theta} \}$ with $\bar{\theta}$ no on the boundary of $\theta$, let also $S\in \mathcal M$ so that $\bar{\theta} = \dot{\theta}$ and define 
$$
\psi(t;\theta) = - \left( \frac{d}{dt}\epsilon(t;\theta) \right)^{T}
$$
>[!note]
>If all the involved processes are [[Stationary process]] then $\psi$ will also be.

We can define
$$
\bar{R}=\mathbb  E[\psi(t;\dot{\theta})\psi(t;\dot{\theta})^{T}]
$$
It can be shown that for a large value of $N$, the variance of the PEM estimator is given by $\bar{P}/N$
$$
\sqrt{ N }(\hat{\theta}_{N}-\dot{\theta}) \sim \mathcal N(0,\bar{P})
$$
We can also estimate the variance
$$
\text{Var}[\epsilon(t;\theta)] = \frac{1}{N}\sum\epsilon(t;\hat{\theta}_{N})^{2}
$$

### Model validation

The identification procedure selects the *best* model belonging to a certain model family. However, we need to ascertain if this model is sufficiently good.
- Is the model sufficiently in agreement with the observed data?
-  Is the model sufficiently good for the purpose it is meant for?
-  Is the model sufficiently flexible (to encompass the true system)?

>[!warning]
The last question is undecidable from a philosophical point of view.

What really matters is the second question: the model is good if it allows to solve satisfactorily the problem that motivated its construction. To validate a model we could, for example simulate it with some controlled input and check its validity with the bode diagram and checking the spectral response. Another approach is to use statistical tests on the residual.

>[!warning]
>Obviously, simulation only works when there is an input $u(t)$

Given a function we want to identify a model for
$$
\hat{y}(t) = f(y(t-1),\dots,u(t-1),\dots)
$$
And let $\epsilon(t)$ be the signal to be tested and calculate
$$
 \gamma_{N}(\tau)= \frac{1}{N}\sum_{1}^{N-\tau}\epsilon(\tau)\epsilon(t + \tau)
$$
To validate the model we need to look at the covariance function also called the **normalized sample covariance function**, that can be calculated by
$$
\hat{\rho}(\tau) = \frac{\hat{\gamma}(\tau)}{\hat{\gamma}(0)}
$$
>[!warning]
For this calculation, we need to use a small number of $\tau$, because the higher $\tau$ is, the less data we can use to calculate the average.

If $\epsilon(t)$ is a [[White noise]] then, for values of $\tau>0$, $\hat{\rho}(\tau)$ has a probability distribution that asymptotically tends to a $\mathcal N(0,1/N)$ so
$$
\sqrt{ N }\hat{\rho}(\tau) \sim \mathcal  N(0,1)
$$
Now to test the model we use the **Anderson tests**. Let the null hypothesis $\mathcal H_{0}$ be that the residual is white
1) Fix the probability that $\mathcal H_{0}$ is rejected while true, this is the confidence level $\alpha$
2) Find the value $\beta$ for which the tails of the standard gauassian outside the interval $(-\beta,\beta)$  has area equal to $\alpha$
$$
\int_{-\beta}^{\beta} \frac{1}{\sqrt{ 2\pi }} e^{-y^{2}/2}  \, dy = 1- \alpha 
$$
3) Count the points of $\hat{\rho}(\tau)$ fall outside the interval $\left( -\frac{\beta}{\sqrt{ N }}, \frac{\beta}{\sqrt{ N }} \right)$
4) If the fraction of points $n_{out}/n <\alpha$, we can accept the hypothesis

If the model is correct, then the residual and the input should be independent
$$
\gamma_{\epsilon u}(\tau|\tau\geq 0) = \mathbb  E[\epsilon(t+\tau)u(t)] \approx 0
$$
For $\tau <0$ the auto correlation function can be either null of not depending on the auto correlation of $u(t)$ 
The sample cross correlation is given by
$$
\hat{\gamma}(\tau) = \frac{1}{N} \sum_{1-\max(\tau, 0)}^{N-\max(\tau, 0)} \epsilon(t+\tau)u(t)
$$
and the normalized cross correlation function is
$$
\hat{\rho}_{\epsilon u}(\tau) = \frac{\hat{\gamma}_{\epsilon u}(\tau)}{\sqrt{ \hat{\gamma}_{\epsilon}(0) \hat{\gamma}_{u}(0) }}
$$
and just apply the Anderson tests.
### Selection of model complexity

In the [[Prediction#Prediction error minimization]] identification process, we first have to pick a model family, and then we identify the best model in that category. In other words, $J(\hat{\theta})$ is an indicator of the adherence of the estimated model to the data. If we increase the model complexity, the degrees of freedom also increase, but is the larger model better? This is the [[Supervised learning#Bias-Variance trade-off]].

>[!note]
The model that we need to pick, from the slides, seems to be the first solution where the whiteness test passes 

The cross validation approach consists in dividing the data in two parts, training and validation sets. While $J(\hat{\theta})$ evaluated on the identification data is a decreasing function of the model complexity, the same evaluated on the validation is not. If the model is too complex the model will not fit well due to overfitting.

```math
||{"id":1123731415250}||


```
More often than not we don't have a lot of spare data to divide for cross validation purposes. To evaluate the data only using the identification data we use some criterion from the ones mentioned below.
#### Final prediction error criterion

Data are realization of [[Stochastic process]] $y(t)=y(t;s), \hat{y}(t) = \hat{y}(t;s;\theta)$. For an objective [[System#Model validation]] we should average over different realizations, so 
$$
\hat{J}(\theta )= \mathbb  E[(y(t;s)-\hat{y}(t;s;\theta))^{2}]
$$
But in practice we are able to minimize only one realizations -- the one we got from the available data.
$$
J_{N}(\theta) = \frac{1}{N}\sum \epsilon(t;\theta)^{2}
$$
Therefore the model is also dependent on the outcome of the random experiment $\hat{\theta}_{N} = \hat{\theta}_{N}(s)$ and to average all the possible data sequences we can just take the average 
$$
FPE = \mathbb  E[\hat{J}(\hat{\theta}_{N}(s))]
$$
The optimal [[System#Selection of model complexity]] is the one that minimizes this criterion.

>[!note]
>The FPE for an [[Autoregressive process]] $AR(n)$ is $FPE = n \lambda^{2} /N + \lambda^{2}$. If $\lambda$ is not known, when using the unbiased predictor for the variance we get $FPE = \frac{N+n}{N-n}J(\hat{\theta}_{N})$
#### Akaike information criterion

With this criterion we want to minimize the distance between the true probability density of the data and the one that would be generated by a given model
$$
AIC= \ln(J(\hat{\theta}_{N})) + 2 \frac{n}{N}
$$
and we still want to minimize this function to get the optimal $n$
#### Minimal description length

The idea is that the optimal complexity of the model should be such that the complete description of the data by means of the model and the prediction error requires the minimum amount of bits
$$
MDL = \ln (J(\hat{\theta}_{N})) + \frac{\ln(N)n}{N}
$$
>[!tip]
>For large values of $n$ the MDL works better then the other criterion, but for small values they are better.


