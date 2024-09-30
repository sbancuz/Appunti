---
tags:
  - machine_learning
---
A more optimized solution for computing the guess is gradient descent, or even better the **stochastic gradient descent**. The stochastic methods is the same as the normal gradient descent, but it doesn't use all the data points, this helps with both speed and performance of learning.

If the loss function can be expressed as a sum over sample where $k$ is the iteration and $\alpha$ is the learning rate
$$
\begin{align}
L(x)  & = \sum L(x_{n}) \\
w^{k+1}  & = w^{k} - \alpha^{k}\triangledown L(x_{n} ) \\
w^{k+1}  & = w^{k} - \alpha^{k}\triangledown (w^{(k)T}\phi(x_{n}) - t_{n})\phi(x_{n}) \\
\end{align}
$$
For convergence the learning rate has to satisfy
$$
\begin{align}
\sum \alpha^{k}  & = \infty \\
\sum \alpha^{k^{2}}  & < \infty
\end{align}
$$To improve the regression process in order to not over-fit too much we can use [[Ridge regression]].