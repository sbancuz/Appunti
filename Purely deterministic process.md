---
tags:
  - mida
---
A process is purely deterministic when, given an arbitrary number of samples, then I can perfectly derive other *newer* samples.
$$
v(t) = a_{1}v(t-1) + a_{2}v(t-2) + \dots + a_{n}v(t-n)
$$
and we can rewrite it in mixed operatorial notation
$$
v(t) = a_{1}z^{-1}v(t) + \dots + a_{n}z^{-n}v(t) \implies (1 - a_{1}z^{-1} - \dots - a_nz^{-n})v(t) = 0 \implies P(z)v(t) = 0
$$
and this can only happen if 
$$
v(t) = \alpha_{1} \lambda_{1}^{t} + \dots + \alpha_{n}\lambda_{n}^{t}
$$
where $\lambda_{i}$ are the zeros of $P(z)$ that is a **stable process**. 

>[!warning]
>Since we are only interested in stationary processes, the condition $|\lambda_{i}| = 1$ must hold

