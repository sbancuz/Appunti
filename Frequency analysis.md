---
tags:
  - mida
---
A process can be always interpreted by looking at it's spectrum that evaluates the function in the frequency domain. 
```math
||{"id":413576829101}||


```
But this only holds in the **deterministic** case, in the **stochastic** one a probability distribution can have multiple realizations
```math
||{"id":1307075696711}||


```
### Spectrum

The **power spectral density** or spectrum of a stationary stochastic process is the [[Fourier transform]] of the correlation function
$$
\Gamma(\omega) = \mathcal  F[\dot{\gamma}(\tau)] = \sum \dot{\gamma}(\tau)e^{-j\omega \tau}
$$
The sum of the [[Serie di Fourier|Fourier series]] exists only for stationary processes whose correlation function $\gamma(\tau)$ tends to $0$ sufficiently rapidly when $\tau$ tends to infinity. A sufficient condition for the existence of the Fourier transform is the absolute convergence of $\gamma(\tau)$.
The anti-transformation formula then becomes
$$
\dot{\gamma}(\tau) = \mathcal F^{-1} [\Gamma(\omega)] = \frac{1}{2\pi} \int _{-\pi}^{\pi}  \Gamma(\omega)e^{j\omega \tau}\, dx 
$$

From the definition it follows that
$$
\Gamma(\omega) = \dot{\gamma}(0) + 2 \dot{\gamma}(1)\cos(\omega) + 2 \dot{\gamma}(2)\cos(2\omega) + \dots + 2 \dot{\gamma}(n)\cos(n\omega)
$$
Therefore $\Gamma(\omega)$ is a **real, even, non-negative** and **periodic** function. 

>[!note]
The maximum angular frequency for sinusoidal discrete time signals is $\omega_{max} = \pi$, thus the minimum period is $T = 2$.

For processes with $\mathbb E = 0$ the variance of the process is equal to the area below the spectral density curve.
$$
\gamma(0) = \frac{1}{2\pi} \int _{-\pi}^{\pi} \Gamma(\omega)\, dx 
$$
The spectrum can be defined in two steps:
1)  Take the bilateral $\mathcal Z$ transform of the correlation function
$$
\phi(z) = \sum \dot{\gamma} z^{-\tau}
$$
2) Evaluate $\phi(z)$ in $z=e^{j\omega}$

>[!info]
>$\phi(z)$ is noted as the **complex spectrum**

For stationary processes obtained by filtering white noise through a dynamical system (e.g., [[Moving average process]], [[Autoregressive process]], and [[ARMA process]]) the spectrum can be calculated using the transfer function.

Consider $y(t)$ obtained by filtering the input process $u(t)$ through an asymptotically stable dynamical system $W(z)$. It can be shown that the spectrum of $y$ and $u$ are related by
$$
\Gamma_{yy} (\omega)= |W(e^{j \omega})| ^{2}  \Gamma_{uu}(\omega)
$$
**proof on the slides, too long don't care** 