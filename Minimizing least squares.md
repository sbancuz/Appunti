---
tags:
  - machine_learning
---
Given a data set with $N$ samples, let us consider the following loss function
$$
L(w) = \frac{1}{2} \sum^{N}(y(x_{n}, w) - t_{n})^{2}
$$
This is the residual sum of squares (RSS), aka the sum of squared errors.
$$
J(\theta) = RSS(w) = || \epsilon||_{2}^{2} = \sum^{N} \epsilon^{2}_{i} 
$$
Let's write $RSS$ in matrix form with $\phi = (\phi(x_{1}), \dots, \phi(x_{n})) ^T$ and $t = (t_{1},\dots,t_{n})^{T}$
$$
L(w) = \frac{1}{2} RSS(w) = \frac{1}{2} (t-\phi w)^{T}(t-\phi w)
$$
with the first and second derivative being
$$
\frac{\delta L(w)}{\delta w} = -\phi^{T}(t-\phi w) \qquad \frac{\delta^{2} L(w)}{\delta^{2} w} = \phi^{T}\phi
$$
Assuming that the second derivative is **non singular**
$$
\hat{\theta} = \hat{w}_{OLS} = (\phi^{T}\phi)^{-1}\phi^{T}t 
$$

>[!info] Time [[Complexity of an algorithm]]
>$O(nm^{2} + m^{3})$ 

To improve the regression process in order to not over-fit too much we can use [[Ridge regression]].
### Properties
- The estimate $\hat{w}_{OLS}$ is **unbiased**
- The uncertainty of the model can be estimated by $\text{Var}[\hat{\theta}] = \lambda^{2}(\phi^{T}\phi)^{-1} = \lambda^{2} R(N)^{-1}$
- An estimate of $\hat{\lambda}^{2}$ is $\frac{J(\hat{\theta})}{N -n}$ where $N$ is the number of data and $n$ is the number of regressors 
