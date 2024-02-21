---
tags:
  - mida
---
We have a [[Modeling]] problem $\theta$, which can be any function or constant --even of time, and a set of observations $d$ over time $T$
$$
\theta \qquad d = \{ d(t_{1}),\dots,d(t_{n}) \} \qquad T = \{ t_{1}, \dots, t_{n} \}
$$
The object of an estimation problem is to produce an estimator 
$$
\theta = f(d) \leftarrow \text{estimator}
$$
A value of $\theta$ produced by the estimator is an **estimate**. This estimate can either be:
- constant $\to$ $\hat{\theta} \approx \theta^{0}$
- time dependent $\to$ $\hat{\theta}(t|T), \hat{\theta}(t|t_{n})$

When $t > t_{n}$ we have a **prediction**, and when $t=t_{n}$ we have **filtering** -- the estimation of a variable for which we already have an estimation. This can be used to perceive the difference of the real observation and the prediction, or it can be used to see the value of other variables that depend on the one predicted. Lastly if $t < t_{n}$ we have a **regularization/interpolation/smoothing**.

>[!example] Navigator's problem
>
>We want to find the position of a ship, given the position of two beacons. This beacons measure the distance from the ship.
>```math
||{"id":951490479100}||
>```
>
>$$
\tau_{i} = \frac{2d_{i}(\theta)}{c} = \frac{2}{d}\sqrt{ (x_{i} - x^{0}) + (y_{i} - y ^{0})}
>$$
>When repeating this experiment, we will have always different results. This is because of noise. We can't remove all of these unknown factors that generate this noise because it would be too costly to model. So to model this noise we can just add some **uncertainty**
>$$
\tau_{i} = \frac{2d_{i}(\theta)}{c} + w_{i}
>$$
>If the ship is moving then we have more problems, so we have to consider intervals using [[Difference equation]]
>$$
>\theta(t + \Delta) = \theta(t) + v(t)\Delta t + w(t)
>$$
### Uncertainty

As already said, in these types of problems we can't model every variable, every noise. So we are dealing with a stochastic problem, and to account for all unknowns in our model we add some **noise term** $w(t)$. 

The most important feature of a noise term is the fact that we don't know it's value a-priori. To resolve this value we can use information from the past to estimate its future. So we can use [[Probability theory]] to do that!

To predict this noise values we can use:
- one or a range of previous values
- recurrence or seasonality
- exogenous variables -- external variable that are correlated to the one we are measuring

To formalize this concept we define
$$
\begin{align}
v(t_{1}), v(t_{2}), \dots, v(t_{n- 1}) &\leftarrow \text{observations $\to$ } v(t)? \\
\hat{v}(t_{n}|t_{n-1}) &= f(v(t_{n - 1}), \dots, v(t_{1}))
\end{align}
$$
where $f$ is a **time invariant linear function**. One observation is that old data, if we don't consider seasonality, may matter less than the new one, so we can use **finite memory prediction**. With this observation the prediction becomes
$$
\hat{v}(t_{n}|t_{n-1}) = a_{1}v(t_{n-1}) + \dots + a_{k}v(t_{n-k})
$$
with all the weights are representing the actual model
$$
\theta = [a_{1},a_{2},\dots,a_{n}]^{T}
$$
so the problem now becomes to find $\theta$, but this is just a [[Model optimization problems]]! But how do evaluate if a model is actually good? The simple idea is to test the model against some actual data and compare the results. In this case the evaluation is given by
$$
\epsilon(t_{i}) = v(t_{i}) - \hat{v}(t_{i}|t_{i-1})
$$
with an evaluation function
$$
J(\theta) = \sum_{n+1}^{N}\epsilon(t_{i})^{2}
$$
and we have to find the best $\theta$ to minimize $J(\theta)$. 
If the residual is all white noise, then we can no longer improve the model and $w(t) = \epsilon(t)$

 To represent the model we can also use the $\mathcal Z$ transform
$$
\begin{align}
V(z)  & = \mathcal Z [v(t_{n})] \\
z^{-1}V(z)  & = \mathcal  Z [v(t_{n - 1})]
\end{align}
$$
This means that the model can be rewritten as
$$
\begin{align}
V(z)  & = \mathcal Z[\dots]   = a_{1} \mathcal Z[v(t_{n-1})] + a_{k} \mathcal Z[v(t_{n-k})] + \mathcal Z[\epsilon(t)]  \\
W(z)  & = \frac{V(z)}{\epsilon(z)}   = \frac{1}{1-a_{1}z^{-1}-\dots-a_{k}z^{-k}} = \frac{z^{k}}{z^{k}- a_{1}z^{k-1} - \dots - a_{k}}
\end{align}
$$
and returning to the time domain
$$
v(t) = a_{1}z^{-1}v(t_{n-1}) + \dots + a_{k}z^{-k}v(t_{n-k}) + \epsilon(t)
$$
