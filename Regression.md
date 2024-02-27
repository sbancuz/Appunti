---
tags:
  - machine_learning
---
The goal of regression is to learn a **mapping** of input $x$ to a continuous output $t$

![[regression.png]]

Many real process can be approximated with **linear models**, even in larger systems. A linear model is in the form of
$$
y(x_{1},\dots,x_{n}) = w_{n}x_{n} + \dots + w_{1}x_{1} + w_{0}
$$
where the weights are called the **features**. The good thing is that we are guaranteed to reach the global minimum of the function, this means that if a linear model is not performing well it's because it doesn't have enough features.

>[!warning]
>The input doesn't need to be linear. Only the weights have to be!!
### Loss function

To quantify how well, or poorly, our model functions, we need to define a function $L(t, y(x))$ and it's average loss is given by
$$
\mathbb E [L]= \iint L(t, y(x)) p(x,t)\, dx   dt 
$$
>[!note]
>The optimal solution, if we have a completely flexible function is the conditional average
>$$
>\mathbb E [L]= \int t p(t|x)\, dx = y(x)
>$$

A common choice for a loss function is the **squared loss function**
$$
\mathbb E [L]= \iint (t - y(x))^{2} p(x,t)\, dx   dt 
$$
which can be generalized as the **Minkowski loss**
$$
\mathbb E [L]= \iint |t - y(x)|^{q} p(x,t)\, dx   dt 
$$
>[!tip]
>The Minkowski loss is better than the quadratic when dealing with a lot of outliers in the data

Depending on $q$ we have:
- Conditional mean $\to$ $q = 2$ 
-  Conditional median $\to$ $q = 1$
-  Conditional mode $\to$ $q= 0$
### Basis function

To consider non-linear functions we can use non-linear basis functions 
$$
y(x, w) = \sum_{1}^{M - 1} w_{j}\phi_{j}(x) = w^{T}\phi(x)
$$
Basics function can be any function, but commonly are used the **Polynomial, Gaussian** and **Sigmoidal**
### Solving the linear regression

We have various approaches:
- **Generative** $\to$ we model the joint density $p(x,t) = p(x|t)p(t)$, infer the conditional density and resolve for the mean
$$
\mathbb  E[t | x] = \int tp(t|x) \, dt 
$$
- **Discriminative** $\to$ we model the conditional density and resolve for the mean
	[[Minimizing least squares]]
	[[Gradient descent]]

- **Direct** $\to$ find $f(x)$ directly from the data
	[[Maximum likelihood]]
### Multiple outputs

It doesn't change much with respect to the single output case, the target will just be a vector $T$ and the basis will be
$$
\hat{w}_{OLS} = (\phi^{T}\phi)^{-1}\phi^{T}T
$$
and for each output we will have
$$
\hat{w}_{OLS} = (\phi^{T}\phi)^{-1}\phi^{T}t_{k} 
$$
