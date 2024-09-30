---
tags:
---
There is a problem, a single [[Perceptron]] can't possibly model complex behaviors, it's just a linear separation boundary in the hypotheses space.  The solution is to make a net of perceptrons that can create a non-linear boundary to correctly give results. Unfortunately Hebbian learning will not work anymore because it can't act on the intermediate or **hidden layers**.

![[FFNN.png]]

Feed forward neural networks must be arranged as acyclic [[Graphs#Directed graphs]], this means that, although networks like the image are more common, there can be some connections that skip layers. In order to make the neural network learn we have to make also another modification: the non-linear function of the perceptron can't be the $sign()$ since it's not differentiable, we have to use some non-linear function that it's differentiable and has also the same rough shape if the outputs needs to be normalized.  Here are a couple of examples of simple activation functions, though the most used today is the RELU.

![[activation functions.png]]

Depending on whether we want [[Regression]] or [[Classification]] our output layer can exhibit different behaviors. In [[Regression]] the output spans the entire $\mathbb R$ domain, but for [[Classification]] we just need a vector with only one $1$ that represents the choice of the network. When dealing with multiple $K$ classes it's better to use the **softmax** as an activation function to have a normalized output that can represent a probability
$$
y_{k} = \frac{exp(z_{k})}{\sum_{k}exp(z_{k})}
$$
### Universal approximation theorem

A single hidden layer feed forward neural network with S shaped activation functions can approximate any measurable function to any desired degree of accuracy on a compact set. So regardless of the function we are learning a single layer can represent it. Two in the case we are dealing with classification. 

>[!warning]
>This doesn't mean that it's a good idea to always only use one hidden layer, but just that it's theoretically possible
### Learning

Recall the learning process of a parametric mode $y(x_{n}| \theta)$ in [[Regression]]/[[Classification]]. We have a training set and we want to find model parameters such that for new data
$$
y(x_{n}|\theta)\sim t_{n}
$$
Or in case of neural networks
$$
g(x_{n}|w)\sim t_{n}
$$
Normally we could use [[Gradient descent]], but $g$ is non-linear, so there are multiple local minima where the minimization could fall into. To avoid some of them we can use momentum, so the weight update function becomes
$$
w^{k + 1} = w ^{k} -\eta \frac{ \partial E(w) }{ \partial w }  - \alpha \frac{ \partial E(w) }{ \partial w } 
$$
To also update the weights of the hidden layers we use **backpropagation**. This can be done in parallel, locally and it requires just 2 passes thanks to the chain rule of the derivative.

![[backprop.png]]
