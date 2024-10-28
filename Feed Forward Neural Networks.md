---
tags:
  - neural_networks
---
There is a problem, a single [[Perceptron]] can't possibly model complex behaviors, it's just a linear separation boundary in the hypotheses space.  The solution is to make a net of perceptrons that can create a non-linear boundary to correctly give results. Unfortunately Hebbian learning will not work anymore because it can't act on the intermediate or **hidden layers**.

![[FFNN.png]]

Feed forward neural networks must be arranged as acyclic [[Graphs#Directed graphs]], this means that, although networks like the image are more common, there can be some connections that skip layers. In order to make the neural network learn we have to make also another modification: the non-linear function of the perceptron can't be the $sign()$ since it's not differentiable, we have to use some non-linear function that it's differentiable and has also the same rough shape if the outputs needs to be normalized.  Here are a couple of examples of simple activation functions, though the most used today is the RELU.

![[activation functions.png]]

Depending on whether we want [[Regression]] or [[Classification]] our output layer can exhibit different behaviors. In [[Regression]] the output spans the entire $\mathbb R$ domain, but for [[Classification]] we just need a vector with only one $1$ that represents the choice of the network. When dealing with multiple $K$ classes it's better to use the **softmax** as an activation function to have a normalized output that can represent a probability
$$
y_{k} = \frac{exp(z_{k})}{\sum_{k}exp(z_{k})}
$$
These functions however are not used in real models because better ones have been found. This is because these types of functions don't work in deep networks since the gradient keeps shrinking the input for every layers it passes through. For this we have the ReLU which is defined as
$$
g(a) = max(0,a) \qquad g'(a) = 1_{a>0}
$$
>[!note]
>There are a number of different variations of the ReLU, but they work all in the same way. 
### Universal approximation theorem

A single hidden layer feed forward neural network with S shaped activation functions can approximate any measurable function to any desired degree of accuracy on a compact set. So regardless of the function we are learning a single layer can represent it. Two in the case we are dealing with classification. 

>[!warning]
>This doesn't mean that it's a good idea to always only use one hidden layer, but just that it's theoretically possible. In practice would be really bad since it's more likely that it will not generalize. See [[Supervised learning#Bias-Variance trade-off]]
### Learning

Recall the learning process of a parametric mode $y(x_{n}| \theta)$ in [[Regression]]/[[Classification]]. We have a training set and we want to find model parameters such that for new data
$$
y(x_{n}|\theta)\sim t_{n}
$$
Or in case of neural networks
$$
g(x_{n}|w)\sim t_{n}
$$
Normally we could use [[Gradient descent]] and [[Maximum likelihood]], but $g$ is non-linear, so there are multiple local minima where the minimization could fall into. To avoid some of them we can use momentum, so the weight update function becomes
$$
w^{k + 1} = w ^{k} -\eta \frac{ \partial E(w) }{ \partial w }  - \alpha \frac{ \partial E(w) }{ \partial w } 
$$
To also update the weights of the hidden layers we use **backpropagation**. This can be done in parallel, locally and it requires just 2 passes thanks to the chain rule of the derivative.

![[backprop.png]]

We can also technically try to solve this analytically using [[Maximum likelihood]]. In the case for [[Regression]] take for instance
$$
t_{n} = g(x_{n}| w) + \epsilon_{n} \qquad \epsilon_{n}\sim \mathcal  N(0, \sigma^{2})
$$
then we can approximate a target function using $t$ as (see also [[Stochastic process#Dynamic representation]] using Wold's decomposition)
$$
t_{n} \sim \mathcal  N (g(x_{n}| w), \sigma^{2})
$$
>[!warning]
>This, however, doesn't paint the right picture since the noise doesn't always have constant noise, this could be due to measurements errors, but for now let's pretend this is not a problem.

I can then use this to compute the log maximum likelihood $l(w)$ and then maximize it with respect to it's weights
$$
argmax_{w}l(w) = argmin_{w}\sum_{n}^{N}(t_{n - g(x_{n}| w)})^{2}
$$
If we remove the previous assumption, what does it happen to the estimator? Well, the distribution becomes very good to represent high-variance data, but bad at representing low variance. This is because high-variance data will impact the mean squared errors more, so even a few outliers can impact the result a lot. To minimize this, *not fix*, is to scale the input data with the $log$.

For [[Classification]] we use the cross-entropy as an error function and as posterior probabilities have to be approximated with
$$
t_{n} \sim Be(g(x_{n}| w))
$$
In this case the maximum likelihood becomes
$$
argmax_{w}l(w) = argmin_{w} \left( - \sum_{n}^{N}t_{n} \log g(x_{n}|w )+ (1 - t_{n} )\log(1-  g(x_{n}|w)) \right) = argmin_{w}\left( -\sum_{n}^{N}t_{n}^{T}\log(g_{n}| w) \right)  
$$
>[!info] Categorical cross-entropy
>Using the vector notation we can extend the likelihood to any sized multivariate output vecors
>
### Initialization

The final result of the gradient descent is highly affected by the starting conditions, so the initialization of the weights matters a lot. 
- All zeros don't work since they will nullify all the gradients, so no learning can happen
- Big numbers are also a bad idea, since they take quite a lot of time to converge
- $w\sim \mathcal N(0, \sigma^{2}=0,01)$ may be good for small networks, but no so much for bigger ones since it can nullify the gradient

Since we know that the variance of the output is the variance of the input scaled by $n \text{Var}(w_i)$ we can normalize the two variances to be the same, this is called **Xavier Initialization**
$$
\underbrace{ w\sim \mathcal N\left( 0, \frac{1}{n_{in}}\right) }_{ Original } \qquad\underbrace{ w\sim \mathcal N\left( 0, \frac{2}{n_{in} + n_{out}}\right) }_{ \text{Glorot \& Bengio} } \qquad\underbrace{ w\sim \mathcal N\left( 0, \frac{2}{n_{in}}\right) }_{ \text{He} } \qquad
$$

