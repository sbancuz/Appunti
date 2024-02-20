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

```math
||{"id":951490479100}||


```

$$
\tau_{i} = \frac{2d_{i}(\theta)}{c}
$$
When repeating this experiment, we will have always different results. This is because of noise. We can't remove all of these unknown factors that generate this noise because it would be too costly to model. So to model this noise we can just add some **unceartainty**
$$
\tau_{i} = \frac{2d_{i}(\theta)}{c} + w_{i}
$$