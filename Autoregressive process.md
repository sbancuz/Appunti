---
tags:
  - "#mida"
---
$$
v(t) = c_{0}v(t) + c_{1}v(t-1) + \dots c_{n}v(t-n) + \eta(t), \qquad \eta \sim \text{Wn} (0, \lambda^{2})
$$
and in operatorial notation
$$
\begin{align}
v(t) &= c_{0}v(t) - c_{1}z^{-1}v(t) - \dots c_{n}z^{-n}v(t) - \eta(t), \qquad \eta \sim \text{Wn} (0, \lambda^{2}) \\
e(t) & =(1 - c_{0} - c_{1}z^{-1} - \dots - c_{n}z^{-n})v(t) \\
	 & = W(z)\eta(t)
\end{align}
$$
where
$$
W(z) = \frac{z^{n}}{z^{n} - a_{1}z^{n-1} - \dots - a_{n}}
$$
>[!warning]
This process is not always asymptotically stable.

When this process is asymptotically stable then $v(t)$ converges to a stationary process, called $\text{Ar}(n)$ which is the only stationary process that solves the defining time function domain equation.
### $\text{Ar}(n)$

An asymptotically stable $\text{Ar}(n)$ model is equivalent to an $\text{Ma}(\infty)$, which is a [[stationary process]]. The solution of the time domain equation asymptotically converges to a stationary process.
#### Yule-Walker equation for $\text{Ar(2)}$
$$
v(t)v(t-\tau) = a_{1}v(t-1)v(t-\tau) + \dots + a_{n}v(t-n)v(t-\tau)
$$
and  its $\gamma$ function will be
$$
\gamma(\tau) = a_{1}\gamma(\tau - 1)  + a_{2}\gamma(\tau - 2) + \begin{cases}
0  & \tau \neq 0 \\
\lambda^{2}  & \tau =0
\end{cases}
$$
So
$$
\begin{cases}
\gamma(0) = a_{1}\gamma(1) + a_{2}\gamma(2) + \lambda^{2} \\
\gamma(1) = a_{1}\gamma(0) + a_{2}\gamma(1) \\
\gamma(2) = a_{1}\gamma(1) + a_{2}\gamma(0)
\end{cases}
$$
![[ARMA process#Vanishing covariance property]]