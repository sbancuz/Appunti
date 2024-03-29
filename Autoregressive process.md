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
### [[Prediction#Prediction error minimization]] for ARX

The ARX predictor equation configures a linear regression 
$$
\mathcal  M(\theta): y(t) = a_{1}y(t-1) + \dots + a_{na}y(t-n_{a} ) + b_{0}u(t-k) + \dots + b_{nb}u(t-k_{0}n_{b}) + \eta(t) = \phi(t)^{T}\theta + \eta(t)
$$
Where $\theta$ are all the parameters $a,b$

Now we can apply the [[Minimizing least squares]]. Indeed we are minimizing
$$
J_{N}(\theta) = \frac{1}{N}\sum \epsilon(t;\theta)^{2}
$$
which corresponds to the PEM criterion $\epsilon(t;\theta) = y(t) - \hat{y}(t|t-1;\theta)$. Therefore the [[Minimizing least squares]] method will estimate asymptotically to the set $\Delta$ of the minimal points of $\bar{J}(\theta) = \mathbb E[\epsilon(t;\theta)^{2}$

Suppose that the system belongs to the ideal case
$$
S: y(t) = \dot{a}_{1}y(t-1) + \dots + \dot{a}_{na}y(t-na) + \dot{b}_{0}u(t-k) + \dots + \dot{b}_{nb}u(t - k - n_{b}) + \eta (t)
$$
If $S$ is a stable systems and the input is a [[Stationary process]] then the output will also be a [[Stationary process]].
$$
\bar{J}(\theta) = \mathbb E[\epsilon(t;\theta)^{2}] = (\dot{\theta} - \theta)^{T}\mathbb E[\phi(t)\phi(t)^{T}](\dot{\theta}-\theta) + \mathbb E[v(t)^{2} ] + 2(\dot{\theta}-\theta)^{T}\mathbb  E[\phi(t)v(t) ]
$$
Since $v(t)$ is a [[White noise]] and $\phi$ and $v$ are uncorrelated it follows that
$$
\bar{J}(\theta) = (\dot{\theta} - \theta)^{T}\mathbb E[ \phi(t) \phi(t)^{T}](\dot{\theta} - \theta) + \lambda^{2}
$$
Since the matrix $\mathbb E[\phi(t)\phi(t)^{T}]$ is semi-definite positive, then $\dot{\theta}$ is necessarily a global minimum of $\bar{J}(\theta)$
There are 2 possible cases
- $\mathbb E[\dots]$ is non singular $\to$ identifiable $\to$ **We can use [[Minimizing least squares]]**
- $\mathbb E[\dots]$ is singular $\to$ non identifiable

It also holds that 
$$
\text{Var}[\hat{\theta}_{N}] = \frac{1}{N}\text{Var}[v(t)]\mathbb E[\phi(t)\phi(t)^{T}]^{-1} = \frac{1}{N}\hat{\lambda}\left[ \frac{1}{N}\sum\phi(t)\phi(t)^{T} \right]^{-1} = \hat{\lambda}^{2} S(N)^{-1}
$$
>[!warning]
>$\frac{1}{N}$ cancels

If $\theta$ is not a [[White noise]], this means that we are not in $S\in \mathcal M(\theta)$ and it also mean that $\theta$ and $\eta$ are correlated, thus the [[Minimizing least squares]] is not consistent anymore.
### [[System#Experimental vs Structural identifiability]]

For static models, the singularity of matrix $S(N)$ indicates the redundancy of one or more regressors -- this is an over parameterized model. Notice that the regressors are strictly related, in fact the output depends on the input and it turns out that a condition only based on $u$ is not sufficient to guarantee identifiability, but we can define at least a **necessary** condition. We define the matrices
$$
\begin{align}
\bar{R}_{uu} = \mathbb E [ [u(t-1),\dots,u(t-n_{b}) ]^{T}[u(t-1),\dots,u(t-n_{b}) ]] \\
\bar{R}_{yy} = \mathbb E [ [y(t-1),\dots,y(t-n_{a}) ]^{T}[y(t-1),\dots,y(t-n_{a}) ]] 
\end{align}
$$
The necessary condition for identifiability is that $\bar{R}_{uu}$ should be invertible.

A signal $u(t)$ is **persistently exciting** of order $n$ if the following Toeplitz matrix is invertible
$$
\bar{R}_{uu}^{n} = \left[\begin{matrix}
\gamma_{uu}(0)  & \gamma_{uu}(1)  & \dots  & \gamma_{uu}(n_{b}-1) \\
\gamma_{uu}(1)  & \gamma_{uu}(0)  & \dots  & \gamma_{uu}(n_{b}-2) \\
\vdots  & \vdots  & \ddots  & \vdots \\
\gamma_{uu}(n_{b}-1)  & \gamma_{uu}(n_{b}-2)  & \dots  & \gamma_{uu}(0) \\
\end{matrix}\right]
$$
To uniquely estimate the parameters of an $ARX(n_{a}, n_{b})$, the input must be $PE(n)$ with $n\geq n_{b}$

>[!note]
>If $n<n_{b}$ then there are multiple estimate parametarizations.

If the estimates fluctuate even for large values of $N$, then presumably the model is over-parameterized.
If the estimates converges, but the residual is not white, then the model is presumably under-parameterized.
