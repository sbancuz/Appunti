---
tags:
  - mida
---
It is sometimes of interest to model non-stationary residual to describe a **drift** phenomenon
$$
w(t) = w(t-1) + \eta(t)
$$
where $w$ is called a **random walk**. One thing that is important to remember is that the variance is not constant
$$
\text{Var} [w(t)] = \text{Var} [w(t-1)] + \lambda^{2} = \lambda^{2}t
$$
and in operatorial notation it can be represented as 
$$
w(t) = \frac{1}{1-z^{-1}}\eta(t)
$$
This is basically a discrete integral of the [[White noise]]. To model equation we have a noise term that becomes
$$
C(z)w(t) = \frac{C(z)}{1-z^{-1}}\eta(t)
$$
giving us 
$$
(1 - z^{-1})A(z)y(t) = (1 - z^{-1})B(z)u(t-k) + C(z)\eta(t)
$$
that in normal notation is 
$$
A(z)\Delta y(t) =B(z)\Delta u(t) + C(z)\eta(t)
$$
