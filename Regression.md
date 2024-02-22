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
where the weights are called the **features**.

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
- **Direct** $\to$ find $f(x)$ directly from the data
### Discriminative
#### Minimizing least squares

Given a data set with $N$ samples, let us consider the following loss function
$$
L(w) = \frac{1}{2} \sum^{N}(y(x_{n}, w) - t_{n})^{2}
$$
This is the residual sum of squares (RSS), aka the sum of squared errors.
$$
RSS(w) = || \epsilon||_{2}^{2} = \sum^{N} \epsilon^{2}_{i} 
$$
Let's write $RSS$ in matrix form with $\phi = (\phi(x_{1}), \dots, \phi(x_{n})) ^T$ 
$$
L(w) = \frac{1}{2} RSS(w) = \frac{1}{2} (t-\phi w)^{T}(t-\phi w)
$$
with the first and second derivative being
$$
\frac{\delta L(w)}{\delta w} = -\phi^{T}(t-\phi w) \qquad \frac{\delta^{2} L(w)}{\delta^{2} w} = \phi^{T}\phi
$$
Assuming that the second derivative is **non singular**
$$
\hat{w}_{OLS} = (\phi^{T}\phi)^{-1}\phi^{T}t 
$$

