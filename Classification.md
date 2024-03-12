---
tags:
  - machine_learning
---
The goal of classification is to assign an input $x$ into one of $K$ discrete $C_{k}$ classes, typically we assign one class to each input.

>[!note] Assumption
>There is no noise in the labels
### Linear classification

In linear classification, the input space is divided into decision regions whose boundaries are called **decision boundaries**. In the linear [[Regression]] case the model is linear in the parameters
$$
y(x,w) = w_{0} + \sum w_{j}x_{j} = x^{T}W + x_{0}
$$
This is not very proper for classification since the domain has to be discrete. We can lie and make everything fit in the $(0,1)$ range or we can just use a **non linear function**
$$
y(x,w) = f(x^{T}w + w_{0})
$$
>[!note]
>This is the activation function of a neuron in [[Neural networks]]

When we have 2 classes we can just have a binary target variable, but this is almost not always the case. If there are $K$ classes, our target variable will be a vector of binary value that contains only one $1$ representing the class. To compute this we have a couple of approaches:
### Direct approach

With a direct approach we use a discriminative function that directly maps the input to some classes. This function is in the form of
$$
y_{k}(x) = x^{T}w_{k} + w_{k0}
$$
> [!note]
> In the case of $x$ being on the decision surface we have
>$$
>\frac{w_{k}^{T}x}{||w_{k}||_{2}} = - \frac{w_{k0}}{||w_{k}||_{2}}
>$$
>Hence $w_{k0}$ determines the location of the decision surface.

To assign $x$ to a class $C_{k}$ we need that $y_{k}(x) >y_{j}(x), \forall {j} \neq {k}$. The resulting decision boundaries are singly connected and convex.

We can use [[Minimizing least squares]] to approximate the conditional expectation $\mathbb E[t|x]$. Each class is described by its own linear model
$$
y_{k}(x) = w_{k}^{T}x + w_{k0}
$$
>[!warning]
>This is not a good method for classification, the nature of linear regression makes it very sensitive for outliers, thus worsening the accuracy of the model.

Another approach to construct a discriminative function is to use the [[Perceptron]] algorithm.

### Probabilistic discriminative approach

Probabilistic discriminative approaches that use probabilities to make decision like for [[Regression]]. This means that we want to predict a result given some value. The posterior probability can be written as a ![[Logistic sigmoid function]]
The idea is to **maximize the probability** of getting the right label
$$
p(t|X,w) = \prod y_{n}^{t_{n}}(1-y_{n})^{1-t_{n}}\qquad y_{n} = \sigma(w^{T}\phi_{n})
$$
Taking the negative log of the likelihood, we can define the **cross entropy error function** to be minimized
$$
L(w) = -\ln p(t|X,w) = -\sum(t_{n}\ln y_{n} + (1-t_{n})\ln(1-y_{n})) = \sum L_{n}
$$
that differentiated becomes
$$
\frac{\delta L_{n}}{\delta w} = (y_{n} - t_{n})\phi_{n} 
$$
so the gradient becomes
$$
\triangledown L(w) = \sum (y_{n} - t_{n})\phi_{n}
$$
and to optimize this we can just use [[Gradient descent]] because this function is **convex**. To extend this notion for multiple classes, we can just use the ![[Softmax]]
### Probabilistic generative approach

Probabilistic generative approach that use the [[Bayes rule]]

