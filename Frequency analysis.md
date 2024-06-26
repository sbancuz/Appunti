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

For stationary processes obtained by filtering [[white noise]] through a dynamical system (e.g., [[Moving average process]], [[Autoregressive process]], and [[ARMA process]]) the spectrum can be calculated using the transfer function.

Consider $y(t)$ obtained by filtering the input process $u(t)$ through an asymptotically stable dynamical system $W(z)$. It can be shown that the spectrum of $y$ and $u$ are related by
$$
\Gamma_{yy} (\omega)= |W(e^{j \omega})| ^{2}  \Gamma_{uu}(\omega)
$$
**proof on the slides, too long don't care** 
### Spectral factorization

The following are 4 different representations of a stochastic processes generated by filtering a [[white noise]] through a stable digital filter:
- time domain $\to$ $v(t) = a_{1}v(t-1) + \dots a_{na}v(t-n_{a}) +c_{1}\eta(t-1) + \dots + c_{nc}\eta(t-n_{c})$
- operatorial $\to$ $v(t) = \frac{C(z)}{A(z)}\eta(t)$
- probabilistic notation $\to$ $\mu, \gamma(\tau)$
- frequency domain $\to$ $\mu, \Gamma(\omega)$

>[!info]
>All of these representations are equivalent!!

We are often given a set of data with certain spectral characteristics and we are faced with the problem of describing the generator process, i.e. of finding the pair $\mu, \Gamma(\omega)$

The problem is that given a spectrum there isn't always a corresponding [[ARMA process]] that represents it, the shape of the spectrum is not completely arbitrary. Also if it happens that the transfer function exists, it wont be unique.

>[!example]
>Consider a generic process $v(t) = W(z)\eta(t)$, the complex spectrum is given by $\phi(z) = W(z)W(z^{-1})\lambda^{2}$
>1) Multiplication by a constant
>$$
>\begin{align} \\
>\dot{W}(z) &= \frac{1}{\alpha} W(z), \qquad \dot{\eta}(t) \sim \text{Wn}(0, \alpha^{2}\lambda^{2}) \\
>\dot{\phi}(z) &= \dot{W}(z) \dot{W}(z^{-1})\alpha^{2}\lambda^{2} = \frac{1}{\alpha} W(z) \frac{1}{\alpha} W(z^{-1}) a^{2}\lambda^{2}=\phi(z)
>\end{align}
>$$
>2) Multiplication by $z^{n}$
>$$
>\begin{align} \\
>\dot{W}(z) &= z^{n} W(z), \qquad \dot{\eta}(t) = z^{-n}\eta(t) \\
>\dot{\phi}(z) &= \dot{W}(z) \dot{W}(z^{-1})\lambda^{2} = z^{n} W(z)z^{-n} W(z^{-1})\lambda^{2} = \phi(z)
>\end{align}
>$$ 

Is there a representation that is **better** than the other ones? 
### Canonical representation

Let $v(t)$ be a [[Stationary process]] with rational spectrum, there exists a unique pair
$$
\left( \hat{W}(z)=\frac{C(z)}{A(z)}, \xi(t) \right)
$$
such that:
- $C(z)$ and $A(z)$ are monic
- $C(z)$ and $A(z)$ have the same degree 
- $C(z)$ and $A(z)$ are coprime
- $C(z)$ and $A(z)$ have all their roots in the closed and open unit circle respectively

$\hat{W}(z)$ takes the name of **canonical spectral factor**.
