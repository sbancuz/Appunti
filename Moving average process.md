---
tags:
  - mida
---
Given a white process $\eta(t)$ with $\mathbb{E}[\eta(t)] = 0$ and variance $\lambda^{2}$, we denote as **MA** process of order $n$ the [[Stochastic process]] defined by 
$$
v(t) = c_{0}\eta(t) + c_{1}\eta(t-1) + \dots c_{n}\eta(t-n), \qquad \eta \sim \text{Wn} (0, \lambda^{2})
$$
In other words, $v(t)$ is the weighted average of the time window. We also have that
$$
\begin{align}
\mathbb E [v(t)] =\text{ }& c_{0}\mathbb E[\eta(t)] + \dots +  c_{n}\mathbb E[\eta(t - n)]  =0 \\
\text{Var}[v(t)] = \text{ }& c_{0}^{2}\mathbb E[\eta(t)^{2}] + \dots +  c_{n}^{2}\mathbb E[\eta(t - n)^{2}] + \\
	 & 2c_{0}c_{1} \mathbb  E[n(t)\eta(t-1)] + \dots + 2c_{n-1}c_{n} \mathbb  E[n(t - n - 1)\eta(t-n)] \\
	  = & \text{ } (c_{0}^{2} + \dots + c_{n}^{2}) \lambda^{2}
\end{align}
$$
>[!warning]
>Remember that $\mathbb E[v_{1}(t)v_{2}(t)] = \mathbb E[v_{1}(t)] \mathbb E[v_{2}(t)]$ due to linearity and $\mathbb E[v(t)^{2}] = \lambda^{2}$

$$
\gamma(\tau) = \begin{cases}
(c_{0}^{2} + \dots + c_{n}^{2}) \lambda^{2}  & \tau =0 \\
(c_{0}c_{1} + \dots + c_{n - 1}c_{n}) \lambda^{2}  & \tau =1 \\
\quad \vdots \\
(c_{0}c_{n}) \lambda^{2}  & \tau =\pm n \\ \\
0  & |\tau| > n
\end{cases}
$$
We can also rewrite in operatorial notation
$$
\begin{align}
v(t) &= c_{0}\eta(t) + c_{1}z^{-1}\eta(t) + \dots c_{n}z^{-n}\eta(t), \qquad \eta \sim \text{Wn} (0, \lambda^{2}) \\
	 & =(c_{0} + c_{1}z^{-1} + \dots + c_{n}z^{-n})\eta(t) \\
	 & = W(z)\eta(t)
\end{align}
$$
More precisely we can write
$$
W(z) = \frac{c_{0}z^{n} c_{1}z^{n-1} + \dots + c*n}{z^{n}}
$$
>[!note]
>All the poles are in $z = 0$ so the system is asymptotically stable
### $\text{Ma}(n)$

The $\text{Ma}(n)$ process is characterized by $n+2$ parameters $c_{0},c_{1},\dots,c_{n},\lambda^{2}$. This representation is redundant since 
$$
\dot{c_{1}} = \alpha, \dot{c_{2}} = \alpha, \dots, \dot{c}_{n}, \dot{\lambda}^{2} = \frac{\lambda^{2}}{\alpha^{2}}
$$
has identical probabilistic characteristics of the first and second order (mean value and covariance). To avoid this redundancy we impose $c_{0} = 1$, so $C(z)$ is a **monic process**
### $\text{Ma}(\infty)$

The $\text{Ma}(\infty)$ is given by
$$
v(t) = \sum c_{i}\eta(t - i)
$$
The expected value is still $0$ but the variance may converge or diverge
$$
\text{Var}[v(t)] = (\sum c_{i}^{2})\lambda^{2} = \gamma(0) \text{ $\gets$ finite}  
$$
														^^ *iff does not diverge*
This means that the $\text{Ma}(\infty)$ has an infinitely long auto-covariance function.

To have an infinitely long auto-covariance function, but with finite number of parameters we need the [[Autoregressive process]]