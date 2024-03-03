---
tags:
  - mida
---
Let $v(t)$ be a stationary stochastic process with unknown probabilistic properties, of which we have a finite realization.
$$
\{ v(1), v(2),\dots,v(N) \}
$$
We want to estimate the probabilistic properties of the real $v(t)$ from this limited dataset
$$
\begin{align}
\mu = \mathbb  E[v(t)] \qquad \to \qquad\hat{\mu} = \hat{\mu}_{N}(v(1), v(2),\dots,v(N)) \\
\gamma(t) = \mathbb  E[(v(t) - \mu)(v(t-\tau) - \mu)] \qquad \to \qquad\hat{\gamma} = \hat{\gamma}_{N}(\tau;v(1), v(2),\dots,v(N)) \\
\end{align}
$$
$\hat{\mu}$ and $\hat{\gamma}$ are called **sample estimators** 
#### Sample mean

A natural sample estimator of the mean would be 
$$
\hat{\mu} = \frac{1}{N} \sum v(t)
$$
Notice that $\hat{\mu}_{N}$ is a random variable so 
$$
\hat{\mu}_{N} = \frac{1}{N}\sum v(t;s)
$$
An estimator is considered **correct** or **unbiased** when the expected value of the estimator is equal to probabilistic property to be estimated
$$
\mathbb E [\hat{\mu}_{N}] = \mu
$$

Is this alone enough to prove that a simple mean is a good estimator of the expected value? $\hat{\mu}_{N}$ is not necessarily close to $\mathbb E[v(t;\bar{s})]$

An estimator is considered **consistent** when the estimate error variance tends to zero as the number of data tends to infinity. For example $\hat{\mu}_{N}$ is consistent if $\mathbb E[(\hat{\mu}_{N}- \mu)^{2}]\to 0$ 

>[!warning]
>This, however doesn't work for all stationary processes

For stationary [[ARMA process]] the mean estimator is consistent. 
$$
\mathbb E[(\hat{\mu}_{N}- \mu)^{2}] = \frac{1}{N^{2}} \sum \gamma(j-i) 
$$
### Sample covariance

The sample estimator for the covariance function could be
$$
\hat{\gamma}_{N}(t) = \frac{1}{N - \tau} \sum^{N-\tau}_{1} v(t) v(t + \tau)
$$
>[!note]
>Note that given $\{ v(1), v(2),\dots,v(N) \}$, then
>- $\hat{\gamma}_{N}(0)$ is constructed based on $N$ elements
>- $\hat{\gamma}_{N}(1)$ is constructed based on $N - 1$ elements
>- $\dots$
>- $\hat{\gamma}_{N}(N- 1)$ is constructed based on $1$ element
>
>This means that it's accuracy decreases with $\tau << N$
### Sample spectral density for [[Frequency analysis]]
$$
\hat{\Gamma} (\omega) = \sum_{-\infty}^{\infty} \hat{\gamma}(\tau) e ^{-j \omega \tau}
$$
But since we don't have enough samples we define it from $[-(N - 1),N - 1]$

>[!note]
>Notice that there are $2$ sources of approximation
>- the sample estimator $\hat{\gamma}_{N}(\tau)$ is used
>- the sum is limited to the $N-1$ terms

We can also use the alternative covariance estimator $\hat{\gamma}_{N'}(\tau)$ 
$$
\hat{\gamma}_{N}(t) = \frac{1}{N } \sum^{N-\tau}_{1} v(t) v(t + \tau)
$$
We get an estimator that 
- $\hat{\Gamma}_{N'}(\omega) \geq 0$
- $\hat{\Gamma}_{N'}(\omega) = \frac{1}{N} |\sum v(t) e^{-j \omega t}|^{2}$ it can be computer with a discrete Fourier transform

This estimator is called the **periodogram**. This has these properties:
- $\mathbb E[\hat{\Gamma}_{N'}(\omega) ] \to \Gamma(\omega)$ is asymptotically correct
- $\text{Var}[\hat{\Gamma}_{N'}(\omega)  - \Gamma(\omega)] \to_{\neq} 0$ so it's not consistent
- The estimation error variance remains large even when the number of data tends to infinity
- Two points of the periodogram are uncorrelated regardless of how close they are

![[periodogram.png]]

This approximation is very noisy, so we can get a *smoother* version of the periodogram by computing the [[Moving average process]] or just using the rolling window technique or a combination of them or of other techniques.
