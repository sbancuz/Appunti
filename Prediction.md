---
tags:
  - mida
---
Another problem related to the estimation of a process is to make prediction of future values. Consider a process with rational spectrum
$$
v(t) = W(z)\eta(t) = \frac{C(z)}{A(z)}\eta(t)
$$
We will denote the estimate as $\hat{v}(t+r|t)$ with $r$ being the **prediction horizon**. In general the predictor will have the following structure
$$
\hat{v}(t+r|t) = f(v(t), v(t-1),\dots)
$$
>[!example]
>We can take the naive approach and consider a predictor constructed as the average of the last samples
>$$
>\hat{v}(t + 1|t) = \frac{1}{3} v(t) + \frac{1}{3}v(t-1) + \frac{1}{3}v(t-2) 
>$$ 
>Is this predictor good? Is it a stationary process? How far is it from optimality?

Our objective is to find the **optimal** predictor
$$
\hat{v}(t+r|t)\begin{cases}
v(t) = W(z) \eta(t) \\
v(t), v(t-1), \dots
\end{cases}
$$
To do this we define the prediction error
$$
\epsilon(t+r) = v(t+r) - \hat{v}(t+r|t)
$$
The optimal predictor is the one that minimizes the **mean square prediction error**, i.e. the variance 
$$
\mathbb E[\epsilon(t)^{2}]
$$
we can express $v(t)$ as
$$
v(t) = W(z)\eta(t)
$$
Suppose that the past of the [[white noise]] is known, then we could estimate 
$$
v(t+r) = w_{0}\eta(t+r) + \dots + w_{r-1}\eta(t+1) +w_{r}\eta(t) + w_{r+1}\eta(t-1) + \dots 
$$
							^^$\alpha(t)$		                                        							^^ $\beta(t)$ 

So $\beta$ can be computed once the past of $\eta$ is known and $\alpha$ depends on the future of $\eta$.

>[!note]
>$\alpha$ and $\beta$ are uncorrelated for the reason above
>

The best prediction for $\alpha(t)$ is given by the expected value, and as such, is $0$. So the optimal predictor $\hat{v}$
is
$$
\hat{v}(t+r|t) = \beta(t)
$$
with error
$$
\epsilon(t+r) = v(t+r) - \hat{v}(t+r|t) = \alpha(t)
$$
We notice that the error $\epsilon$ is actually a [[Moving average process]] so $\mu =0$ and the variance is
$$
\mathbb  E[\epsilon(t+r)^{2}] = (w_{0}^{2} + w_{1}^{2} + \dots + w_{r-1}^{2})\lambda^{2}
$$
>[!note]
>The variance will increase with $r$ and it will limit the prediction error

We can, as always, express this prediction with operatorial notation using
$$
\frac{C(z)}{A(z)} =  W(z) = w_{0} + w_{1} z^{-1} + \dots + w_{r-1}z^{-r+1} + w_{r}z^{-r} + \dots = E(z) + z^{-r}\hat{W}_{r}(z)
$$
>[!warning]
>The optimal predictor that we found depends on the past values of the [[white noise]]. However these are not generally available.

Assume that:
- $W(z), \eta(t)$ is a canonical representation of $v(t)\to \hat{W}(z) = W(z), \xi(t) = \eta(t)$
- $W(z)$ has no zero on the unit circle, equivalently $\Gamma(\omega) >0$

Then we can recover $\eta(t)$ using a **whitening filter**
$$
v(t) = W(z) \eta(t) = \frac{C(z)}{A(z)}\eta(t) \to \eta(t) = \dot{W}(z)v(t) = W(z)^{-1}v(t) = \frac{A(z)}{C(z)} v(t)
$$
We can combine the whitening filter with the optimal predictor to get the transfer function
$$
W_{r}(z) = \hat{W}(z)\dot{W}(z) = \frac{F_{r}(z)}{A(z)} \frac{A(z)}{C(z)} = \frac{F_{r}(z)}{C(z)}
$$
### Initialization

Unless $C(z)$ is trivially $1$ , the optimal predictor from data has the form of a **recursive equation**
$$
\hat{v}(t+r|t) = -c_{1} \hat{v}(t+r - 1|t-1) - c_{2}\hat{v}(t+r-2|t-2) + \dots
$$
We can resolve this recursive equation heuristically by initializing $\hat{v}$ to $\mathbb E[v]$ when the data is not available. Thanks to the asymptotic stability of $W_{r}(z)$ it's effect will vanish in the long run.

>[!warning]
>In case the model is not in canonical form, this prediction will diverge. To fix this we can derive the canonical form by simply inverting the zero and adjusting the noise variance so that the autocovariance function remains unchanged
### Prediction error minimization

The PEM methods are based on the minimization of the residual. Let $\hat{\theta}_{N}$ be the minimum of the cost function $J_{N}(\theta)$. Now since $\epsilon(t)$ depends on the data, assuming that the predictor is stable and that $u(t)$ and $y(t)$ are [[Stationary process]], then $\hat{y}(t)$  will also be stationary. This means that $J_{N}$ is the sample mean value of a stationary process.

>[!note]
>If the process is ergodic, then $J_{N}$ will tend to the expected value

Accordingly, if we denote with $\Delta$ the set of minima of $\bar{J}$, we expect $\hat{\theta}_{N}$ to tend to $\Delta$. In the case that $S\in \mathcal M$ then there exists $\dot{\theta}$ such that $S=\mathcal M(\dot{\theta})$. But does this also imply that $\hat{\theta}\to\dot{\theta}$?

Take the prediction error
$$
\epsilon(t;\theta) = y(t) - \hat{y}(t;\theta) = [y(t) - \hat{y}(t; \dot{\theta})] + [\hat{y}(t;\dot{\theta}) - \hat{y}(t;\theta)]
$$
											^^ *innovation*                   
The **innovation** is the optimal predictor that we could calculate if we knew the true system, and the second term is the combination of two variables that both depend on the past of $u(t),y(t)$, so
$$
\text{Var}[\epsilon(t;\theta)] = \text{Var}[\epsilon(t;\dot{\theta})]
$$
If $\Delta$ is a singleton we can conclude that a PEM method will lead to a model that asymptotically tends to the true system. In reality the models in $\Delta$ are the **best approximation** of $S$

![[singelton mida.png]]
