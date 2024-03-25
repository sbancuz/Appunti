---
tags:
  - mida
aliases:
  - Maximum likelihood method
---
This is an algorithm used to estimate the best quadratic approximation of any arbitrary complex function around some point $\theta_{r}$. 

![[newton mehtod.png]]

To make this approximation we need:
- $V(\theta)|_{\Theta=\theta_{r}} =J(\theta)|_{\Theta=\theta_{r}}$
- $\frac{d}{d\theta}V(\theta)|_{\theta=\theta_{r}} = \frac{d}{d\theta}J(\theta)|_{\Theta=\theta_{r}}$
- $\frac{d^{2}}{d\theta^{2}}V(\theta)|_{\Theta=\theta_{r}} = \frac{d^{2}}{d\theta^{2}}J(\theta)|_{\Theta=\theta_{r}}$

This means that is like a [[Serie di Taylor|Taylor series]] for the function, and it also means that we can rewrite the estimator like
$$
V(\theta) = V(\theta_{r}) + \frac{d}{d\theta}V(\theta)|_{\theta_{r}}(\theta-\theta_{r}) + \frac{1}{2}(\theta-\theta_{r}) \frac{d^{2}}{d\theta^{2}}V(\theta)|_{\theta_{r}}(\theta-\theta_{r})
$$And, thus we can write
$$
V(\theta) = J_{N}(\theta_{r}) + \frac{d}{d\theta}J_{N}(\theta)|_{\theta_{r}}(\theta-\theta_{r}) + \frac{1}{2}(\theta-\theta_{r}) \frac{d^{2}}{d\theta^{2}}J_{N}(\theta)|_{\theta_{r}}(\theta-\theta_{r})
$$
To get the minimum of this function we can just set the derivative with respect to $\theta$ to $0$
$$
\frac{d}{d\theta}V(\theta) = \frac{d}{d\theta}J_{N}(\theta)+ \frac{d^{2}}{d\theta^{2}}J_{N}(\theta)\theta-\theta_{r})
$$
and assign the new value of $\theta_{i}$ as
$$
\theta_{i+1} = \theta_{i} - \left( \frac{d^{2}}{d\theta_{i}^{2}}J_{N}(\theta )\right)^{-1}\left( \frac{d}{d\theta_{i}}J_{N}(\theta_{i}) \right)^{T}
$$
