---
tags:
  - mida
---
All the other models ([[Moving average process]], [[Autoregressive process]], [[ARMA process]], ...)seen are only suitable for representing time series, but they do not allow us to describe phenomena that is subject to influence of other exogenous variables. This mean that all these processes can't take anything in input. 

>[!warning]
>The $u(t)$ is the input variable, and the $v(t)$ becomes $y(t)$ because now it takes an input.

The ARMAX process can be described as such
$$
A(z)y(t) = B(z)u(t-k) + C(z)\eta(t)
$$

```math
||{"id":754213303598}||


```
The general idea is that the process is modeled by an input-output relationship, and the model [[Estimation problem#Uncertainty]] is accounted for by the effect of the [[white noise]] input. A further generalization would be allowing a non-linear $f(x)$.
### [[Prediction]]

Consider the generic ARMAX model at time $t+k$
$$
A(z)y(t+k) = B(z)u(t) + C(z)\xi(t + k)
$$
The procedure for the calculation is the same as for the [[ARMA process]]. First we do a long division of $C(z)$ by $A(z)$ for $k$ steps denoting with $E(z)$ the result and with $F_{k}(z)$ the reset
$$
C(z) = A(z)E(z) + z^{-k}F_{k}(z)
$$
and since both $A(z)$ and $C(z)$ are monic we can derive that
$$
y(t + k) = \frac{F_{k}(z)}{C(z)}y(t) + \frac{B(z)E(z)}{C(z)}u(t) + E(z)\xi(t+ k)
$$
hence the optimal $k$-steps ahead predictor is equal to
$$
\hat{y}(t+k|t) = \frac{F_{k}(z)}{C(z)}y(t) + \frac{B(z)E(z)}{C(z)}u(t)
$$
