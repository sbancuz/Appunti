---
tags:
  - machine_learning
---
This is a type of [[Classification#Linear classification]]. It's an online algorithm that corresponds to a linear classification model
$$
y(x) = f(w^{T}\phi(x)) \qquad f(a) = \begin{cases}
+1 & a\geq 0 \\
-1  & a<0
\end{cases}
$$
that tries to find a **separating hyperplane** by minimizing the distance of misclassified points to the decision boundary. 

>[!warning]
>Using the number of misclassified points as a loss function is not effective since it's a piecewise constant function

The perceptron criterion assigns 
- a zero error to correct classifications
- $w^{T}\phi(x_{n})t_{n}$ to misclassified patterns $x_{n}$, so it's proportional to the distance to the decision boundaries

Now the loss function becomes
$$
L_{P}(w) = - \sum w^{T}\phi(x_{n})t_{n}
$$
and it gets minimized using [[Gradient descent]]

>[!note]
>$t_{n}$ corresponds to the $f(a)$ from above, and it's just used to adjust the sign of the weights

If the problem is linearly separable, then this algorithm will converge to the result, but this also mean that if it's not, it will not terminate. The problem is that the termination of this algorithm is **non decidable**.