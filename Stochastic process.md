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
#### Properties
- The $\mathbb E$ is a linear function
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
>The square root of the variance is called the [[Standard deviation]] $\lambda$

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
### Dynamic representation

If we consider a constant process $v(t,s) = v(s)$ as an example of a [[Purely deterministic process]], in contrast white noise is an example of **completely unpredictable process**. For any give process $v(t)$ we can decompose it as
$$
v(t) = \dot{v}(t) + \hat{v}(t)
$$
                                                            ^^     ^^ *purely independent component*
                                                            ^^  *purely deterministic component*
Where
$$
\begin{align}
\hat{v}(t) &= \sum_{-\infty}^{t} w(t,i)\eta(i) & \eta(x) \sim \text{Wn}(0, \lambda^{2}) \\
& = \sum_{-\infty}^{t} w(t-i) \eta(i) \\&=_{k = t-i} \sum_{-\infty}^{t}w(k)\eta(t-k)
\end{align}
$$

So we can think of a system as
```math
||{"id":429443279350}||


```
Also we can rewrite it with the $\mathcal Z$ transform
$$
\hat{v}(t) = (w(0) +z^{-1}w(1) + z^{-2}w(2) + \dots ) \eta(t) = W(z)\eta(t)
$$
With $W(z)$ as the [[Transfer function]] of a stable system. This means that if $w(z)$ is stable then $\hat{v}(t)$ must be **stationary**.

Because $\hat{v}(t)$ and $\dot{v}(t)$ are independent we have that
$$
\mathbb  E [\dot{v}(t_{1})\hat{v}(t_{2})] = \mathbb  E[\dot{v}(t_{1}) ] \mathbb E[\hat{v}(t_{2})] = 0
$$
																	^^ *This is equal to zero*
$$
\dot{\gamma}_{v} (\tau) = \mathbb E[v(t)v(t+\tau)] = \mathbb E[\dot{v}(t)\dot{v}(t+\tau)] + \mathbb E[\hat{v}(t)\hat{v}(t+\tau)] = \dot{\gamma}_{\dot{v}} (\tau) + \dot{\gamma}_{\hat{v}} (\tau)  
$$

Consider a linear time-invariant dynamical system with input $u(t)$ and output $y(t)$
```math
||{"id":1599305467337}||


```
The output of the system is the sum of the free motion $y_{L}(t)$ and the forced motion $y_{F}(t)$
$$
y(t) = y_{L}(t) + y_{F}(t)
$$
Where  
$$
y_{F}(t) = \sum_{t_{0}}^{t} w(t-j)u(t)
$$
and $w(i)$ are the samples of the impulse response of the system. And the system can be rewritten with $\mathcal Z$
$$
Y(z) = W(z)U(z)
$$
																	^^ *this is 1 because u(t) is an impulse*
If the system is **asymptotically stable**, then the free motion goes to $0$. In other words when the system is asymptotically stable then when $t_{0}$ diverges to $-\infty$ we have
$$
y(t) = \sum_{0}^{\infty}w(i)u(t-i)
$$
The [[Frequency analysis]] of a mixed process is given by
$$
\dot{\gamma}_{v}(\tau) = \dot{\gamma}_{\dot{v}}(\tau) + \dot{\gamma}_{\hat{v}}(\tau)
$$
which implies 
$$
\dot{\Gamma}_{v}(\omega) = \dot{\Gamma}_{\dot{v}} (\omega)+ \dot{\Gamma}_{\hat{v}}(\omega)
$$
