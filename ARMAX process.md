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
The general idea is that the process is modeled by an input-output relationship, and the model [[Estimation problem#Uncertainty]] is accounted for by the effect of the white noise input. A further generalization would be allowing a non-linear $f(x)$.