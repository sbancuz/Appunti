---
tags:
  - machine_learning
---
This is another approach to compute regression, the output variable $t$ can e modeled as a deterministic function $y$ of the input $x$ and a random noise $\epsilon$
$$
t = f(x) + \epsilon
$$
with the objective of approximating $f(x)$ with $y(x,w)$ assuming $\epsilon \sim \mathcal N(0, \sigma^{2})$. Now given the $N$ samples, the likelihood function is
$$
p(t|X,w,\sigma^{2}) = \prod \mathcal N (t_{n}|w^{T}\phi(x_{n}), \sigma^{2})
$$
Assuming the samples to be **independent and identically distributed** we can consider the log-likelihood
$$
l(w) = \ln(p(t|X,w,\sigma^{2})) = -\frac{N}{2}\ln(2\pi\sigma^{2}) - \frac{1}{2\sigma^{2}}RSS(w)
$$
To find the maximum likelihood, we equal the gradient to $0$
$$
\begin{align} 
\triangledown l(w) = &  \sum t_{n}\phi(x_{n})^{T} - w^{T}\left( \sum\phi(x_{n})\phi(x_{n})^{T} \right) = 0 \\
\hat{w}_{ML} =  & (\phi^{T}\phi)^{-1}\phi^{T}t 
\end{align}
$$
To compute the maximum likelihood we assume a couple of things:
- $t$ are uncorrelated and have variance $\sigma^{2}$
- the $x_{i}$ are fixed, not random
$$
\text{Var}(\dot{w}_{OLS}) = (\phi^{T}\phi)^{-1}\sigma^{2}
$$
with $\sigma^{2}$ is estimated by
$$
\sigma^{2} = \frac{1}{N-M} \sum (t_{n} - \dot{w}^{T}\phi(x_{n}))^{2}
$$
Assuming also that the model is linear in the features $\phi_{1},\dots,\phi_{M}$ that the noise is additive and Gaussian
$$
\dot{w}\sim \mathcal N(w, (\phi^{T}\phi)^{-1}\sigma^{2}) \qquad (N-M)\sigma^{2} \sim \sigma^{2}x^{2}_{N - M}
$$
If the number of features $M$ is larger than the number of values $N$, then the **variance matrix** will be singular and, thus, cannot compute this. Because some eigenvalues will be $0$ and as such, the matrix won't be invertible. Same if the features are linearly independent.

>[!note] Gauss-Markov Theorem
>The least squares estimate of $w$ has the smallest variance among all **unbiased estimator**.

This does not mean that this is the best method because unbiased estimator are not very good since they usually have a lot of variance in respect to a **bias estimator**.

See also: [[Newton method|Maximum likelihood method]]