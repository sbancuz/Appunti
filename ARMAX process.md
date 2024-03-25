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
### [[System#Prediction error minimization]]

Consider the generic ARMAX model
$$
\begin{align}
\mathcal  M(\theta) :y(t)  = \text{ }& a_{1}y(t-1) + \dots a_{ny(t-n_{a})} \\
  &+ b_{0}u(t-k) + \dots + b_{nb}u(t-k-n_{b})  \\
 & + \eta(t) + c_{1}\eta(t-1) + \dots + c_{nc}\eta(t-n_{c})

\end{align}
$$
>[!warning]
>We could still formulate the model as a linear regression
>$$
>y(t) = \phi(t)^{T}\theta + \eta(t)
>$$
>But $\phi(t)$ will contain variables which are not available.  

We can still formulate this is polynomial form
$$
\mathcal  M(\theta): A(z)y(t+k) = B(z)u(t) + C(z)\xi(t + k)
$$
And let $\theta = [a_{1}\dots a_{na}b_{0}\dots.b_{nb}c_{1}\dots.c_{nc}]^{T}$ be the vector of all the unknown parameters based on both the input and the output.  

In the PEM framework, the optimal parameter estimate is given by
$$
\hat{\theta}_{N} = \text{argmin}\{ J_{N}(\theta) \} \qquad J_{N}(\theta) = \sum \epsilon(t)^{2}
$$
Now the optimal 1 step predictor is given by 
$$
\hat{\mathcal  M}(\theta) : \hat{y}(t|t-1) = \frac{C(z) - A(z)}{C(z)}y(t) + \frac{B(z)}{C(z)}u(t-k)
$$
which due to the denominator makes $J_{N}$ not quadratic in $\theta$ anymore. This means that analytic minimization is not feasible anymore. We can just a numerical approach for minimization like the [[Newton method]]. To apply this method we need to define what are the first and second derivative of $J_{N}$
$$
\begin{align}
\frac{d}{d\theta}J_{N}(\theta)  & = 2 \sum \epsilon(t) \frac{d\epsilon(t)}{d\theta} \\
\frac{d^{2}}{d\theta^{2}}J_{N}(\theta)  & = 2 \sum \frac{d\epsilon(t)}{d\theta}^{T}\frac{d\epsilon(t)}{d\theta}  + 2\sum \epsilon(t) \frac{d^{2}}{d\theta^{2}}\epsilon(t)
\end{align}
$$
>[!tip]
>The second term of the second derivative can be omitted and still provide a *good enough* approximation. If ever the [[Ottimizzazione per funzione di più variabili#Matrice Hessiana|Hessian]] is numerically badly conditioned --close to a singular matrix -- then we can just add a small portion of an identity matrix.

Let us define 
$$
\psi(t) \equiv - \frac{d}{d\theta}\epsilon(t)^{T} = [\alpha_{1}(t)\dots \alpha_{na}(t)\beta_{0}(t)\dots\beta_{nb}(t)\gamma_{1}(t)\dots\gamma_{nc}(t)]
$$
now the update equation becomes 
$$
\theta_{i+1} = \theta_{i} + \left( \sum \psi(t) \psi(t) ^{T}\right)^{-1} \sum \psi(t)\epsilon(t)
$$
and the residual can be simply obtained, similarly as when we were using the [[Minimizing least squares]] method, by
$$
\epsilon(t) = y(t) - \hat{y}(t|t-1) = \frac{A(z)}{C(z)}y(t) - \frac{B(z)}{C(z)}u(t-k)
$$
Now the problem is to find all of these coefficients. First, $\alpha_{i}$ can be found by deriving $a_{i}$ since both $B(z)$ and $u$ do not depend on it. So
$$
C(z)\alpha_{i}(t) = y(t)
$$
Similarly we can find that $\beta_{i}$ can be calculated using the derivative of $b_{i}$
$$
C(z)\beta_{i}(t) = u(t-k)
$$
and lastly deriving in respect to $c_{i}$ we find that 
$$
C(z)\gamma_{i}(t) = \epsilon(t)
$$
And by filtering all the elements through the transfer function $1/C(z)$ we can define 
$$
\psi(t) = \frac{1}{C(z)}\phi_{E}(t)
$$
where $\phi_{E}(t) = [y(t-1)\dots y(t-n_{a})u(t-k)\dots u(t-k-n_{b})\epsilon(t-1)\dots\epsilon(t-n_{c})]^{T}$

>[!note]
>$\phi_{E}(t)$ can also express the prediction error in a simpler form $\epsilon(t) = y(t)-\phi_{E}(t)^{T}\theta$

![[armax newton method.png]]

>[!warning]
>Since this is an iterative approach, there is no guarantee that $\frac{1}{C(z)}$ will have all roots inside of the unit circle, no matter the starting conditions.

To fix this possibility of instability whenever the $C(z)$ polynomial is not a Schur polynomial anymore, we can either
- Take the canonical factor of $C(z)$, although it's computationally intensive $\to$ [[Prediction#Initialization]]
- Bisect the $c_{i}$ coefficients
### Initialization

Since this is an iterative approach, the starting conditions matter a lot, even for convergence. This is because although convergence to a minimum is guaranteed, we can only guarantee that that minimum is a local one, so different initialization may yield different convergences. Using the extended observation vector we can write
$$
y(t) = \phi_{E}(t)^{T}\theta + \eta(t)
$$
If only we knew $\phi_{E}$ then would could just apply the [[Minimizing least squares]] method to calculate
$$
\hat{\theta} = \left( \sum\phi_{E}(t)\phi_{E}(t)^{T} \right)^{-1} \sum \phi_{E}(t)y(t)
$$
The problem is that we can't know the series of $\eta(t)$ but we can estimate it. Consider the model class
$$
\mathcal  M(\theta): \frac{A(z)}{C(z)}y(t) = \frac{B(z)}{C(z)}u(t-k) + \eta(t)
$$
If I think of my two transfer functions as infinitely long polynomials, then we can assume that they can be well approximated by sufficiently large polynomials 
$$
\hat{\mathcal  M}: \hat{A}(z)y(t) = \hat{B}(z)u(t-k) + \eta(t)
$$
and apply [[Minimizing least squares]] on that and use its residual to estimate $\hat{\eta}(t)$. This is like trying to estimate the ARMAX model with an ARX one just to estimate the initial condition of the system.
