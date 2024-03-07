---
tags:
  - mida
---
The series combination of an [[Autoregressive process]] and a [[Moving average process]] model obeys the following equation
$$
v(t) = a_{1}v(t-1) + a_{2}v(t-2) + \dots + a_{na}v(t-n_{a}) + c_{0}\eta(t) + c_{1}\eta(t-1)+ \dots + c_{nc}\eta(t-n_{c}) \qquad \eta \sim \text{Wn}(0, \lambda^{2}) 
$$
and with operatorial notation
$$
x(t) = \frac{1}{A(z)}\eta(t)  \qquad v(t) = C(z)x(t)
$$
with
$$
A(z) = 1 - a_{1}z^{-1} - \dots - a_{na}z^{-na} \qquad C(z) = c_{0} + c_{1}z^{-1} + \dots+ c_{nc}z^{-nc}
$$
The resulting function will be
$$
v(t) = \frac{C(z)}{A(z)} \eta(t) \qquad W(z) = \frac{C(z)}{A(z)}
$$ 
>[!note]
>This is stable if all the roots of the polynomial $W(z)$ are inside the unit circle

The ARMA process can be defined with $\text{Arma}(n,m)$
										   ^     ^ *ma*
										   ^ *ar*

The ARMA process can also be viewed as a $\text{Ma}(\infty)$ process and it implies the usual condition on the coefficients $w_{i}$
### Vanishing covariance property

All the $\text{Ma,Ar,Arma}$ processes share the property that 
$$
\lim_{ \tau \to \infty } {\gamma(\tau)} =0
$$
### [[Prediction]]

Consider
$$
A(z)v(t) = C(z)\eta(t)
$$
where both $A(z),C(z)$ are monic polynomials of the same degree and that all their roots are inside the unit circle. To calculate the 1-step predictor we can apply one step of the long division procedure to the transfer function
$$
W(z) = \frac{C(z)}{A(z)} = 1 + \frac{C(z)-A(z)}{A(z)} = 1 + z^{-1} \frac{z(C(z)-A(z))}{A(z)}
$$
then the optimal 1-step predictor has the following transfer function
$$
W_{1}(z) = \frac{z(C(z)-A(z))}{A(z)}
$$and in the time domain
$$
\hat{v}(t|t-1) = \frac{C(z)-A(z)}{A(z)}v(t)
$$