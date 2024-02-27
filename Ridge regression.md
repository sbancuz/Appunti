---
tags:
  - machine_learning
---
This is a method for reducing the mean square error is to change the loss function as follows
$$
L(w) = L_{D} (w) + \lambda L_{W} (w)
$$
by using the $L_{2}$ norm we get
$$
L(w) = \frac{1}{2} \sum(t_{i} - w^{T}\phi(x_{i}))^{2} + \frac{\lambda}{2}||w||^{2}_{2}
$$
The loss function is still 
$$
\hat{w}_{ridge} = (\lambda I + \phi^{T}\phi)^{ - 1}\phi^{T}t 
$$
![[rigid regression.png|500]]

Another popular regularization method is **lasso**, so using the $L_{1}$ norm. With lasso some parameters can actually reach $0$, and when they do. you can see the parameters that are *less useful*.