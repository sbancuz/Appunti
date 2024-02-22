---
tags:
  - mida
---
A stochastic process is an infinite sequence of [[Probability theory#Random variables]] that depend on the outcome of one random experiment. The simplest form of stochastic process is a [[Stationary process]]
$$
v(t) = \phi(s, t)
$$
Where $s$ is the outcome and $t$ the time.
```math
||{"id":1513490860110}||


```
For every $n \in \mathbb{Z}^{+}$ and for every $n$-tuple of instants $t_{1},\dots,t_{n}$, the joint probability is
$$
F_{t_{1},\dots,t_{n}} (q_{1},\dots,q_{n}) = P (v(t_{1}) \leq q_{1}, \dots, v(t_{n}) \leq q_{n})
$$
and the probability density is
$$
f_{t_{1},\dots,t_{n}} (q_{1},\dots,q_{n})
$$
>[!warning]
>This is too complex
### Expected value

```math
||{"id":458035240467}||


```
The expected value is given by $\mathbb E[\dots]$ and $\mu(t)$ represents the mean at any given moment.
### (Auto-)covariance function

```math
||{"id":1388600853352}||


```
The covariance represents the relation of between values of the same process at different times and is given by 
$$
\gamma(t_{1},t_{2}) = \mathbb E[(v(t_{1}) - \mu(t_{1}))(v(t_{2}) - \mu(t_{2}))]
$$
if we have $t_{1} = t_{2}$
$$
\gamma(t,t) = \mathbb E[(v(t) - \mu(t))^{2}] = \text{variance}
$$
>[!info]
>The square root of the variance is called the [[Standard deviation]]

Notice that
$$
|\text{Cov}[v(t_{1}),v(t_{2})]| \leq \sqrt{ \text{Var}(v(t_{1})) } \sqrt{ \text{Var}(v(t_{2})) }
$$
So let $v = [v(t_{1}), v(t_{2})]^{T}$ then the variance is defined as
$$
\text{Var}[v] = \left[\begin{matrix}
\text{Var}[v(t_{1})]  & \text{Cov}[v(t_{1}), v(t_{2})] \\
\text{Cov}[v(t_{1}), v(t_{2})]  & \text{Var}[v(t_{2})] 
\end{matrix}\right] \geq 0
$$
### (Auto-)correlation
$$
\text{Corr}(t_{1},t_{2}) = \hat{\gamma}(t_{1},t_{2}) = \mathbb E[v(t_{1}) v(t_{2})] = \text{correlation}
$$
and this is also equal to
$$
\hat{\gamma}(t_{1},t_{2}) = \gamma (t_{1},t_{2}) + \mu(t_{1})\mu(t_{2})
$$
### Pearson correlation coefficient

This is also known as the normalized covariance function
$$
\rho(t_{1},t_{2}) = \frac{\gamma(t_{1},t_{2})}{\sqrt{ \gamma(t_{1},t_{1}) } \sqrt{ \gamma(t_{2},t_{2}) }}
$$
By the fact that this value is normalize we have that
$$
|\rho(t_{1},t_{2})| \leq 1, \qquad \rho(t,t) = 1
$$

>[!note]
>The **maximum correlation** is when $\rho = 1,-1$ and the **minimum correlation** is when $\rho = 0$

