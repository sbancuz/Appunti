---
tags:
  - mida
---
A stationary process is a [[Stochastic process]] that can be repeated over time, this means that over some interval the probability distributions are the same. We say that a process is **strongly stationary** if $F_{t_{1},\dots,t_{n}}(\dots) = F_{t_{1 + \tau},\dots, t_{n+\tau}}(\dots)$ and **weakly stationary** if the covariances are stationary.
$$
\mu(t) = \mu(t + \tau) \qquad \gamma(t_{1},t_{2}) = \gamma(t_{1} + \tau, t_{2} + \tau) = \gamma(\tau)\qquad \tau = t_{1} - t_{2}
$$
This means that $\mu$ and the $\text{Var}$ are **constant** and the $\gamma$ is a function of only one parameter.

>[!warning]
>We will always be dealing with weakly stationary processes.
### Properties

- $\mathbb E[v(t)] = \mu$
- $\gamma(\tau) = \mathbb E[(v(t) - \mu)(v(t + \tau) - \mu)]$
- $\hat{\gamma}(\tau) =\mathbb E [v(t)v(t+\tau)]$
- $\gamma(0) = \text{Var}[v(t)]$
- $|\gamma(\tau)|\leq \gamma(0)$
- $\gamma(\tau) = \gamma(-\tau)$ $\gets$ **even function**
### Toeplitz matrix
$$
\left[
\begin{matrix}
\gamma(0)  & \gamma(1)  & \dots  & \gamma(n-1)  \\
\gamma(1)  & \gamma(0)  & \dots  & \gamma(n-2)  \\
\vdots  & \vdots  &  \ddots & \vdots \\
\gamma(n-1)  & \gamma(n-2)  & \dots  & \gamma(0)  \\
\end{matrix}
\right] \geq 0
$$
This matrix can be constructed as $\mathbb E[VV^{T}]$ where 
$$
V = [(v(0) - \mu), (v(1) - \mu), \dots, (v(n-1) - \mu)]^{T}
$$
An even function $\gamma(t)$ can be interpreted as the covariance function of a stationary process iff the associated Toeplitz matrix is positive semi-definite for all values of $N$.
