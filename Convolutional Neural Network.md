---
tags:
  - neural_networks
---
A convolutional neural network uses a **linear filters** -- see [[Image classification]] -- to find local features in the input space in an efficient way. In a CNN underlying data representation is a **volume**. 

![[CNN layer.png]]


The output of a convolutional layer is a linear combination of all in a region of the input, considering all the channels
$$
a(r,c,l) = \sum_{(u,v)\in U,k = 1\dots C} \underbrace{ w^{l}(u,v,k) }_{ \text{Filter} }x(r +u, c+v, k) + \underbrace{ b^{l} }_{ \text{ Filter} }
$$
Filters need to have the same *number of channels* as the input. Here the hyperparameters are
- The spatial extent of the filter
- The number of filters

The number of parameters is given by
$$
(h_{r} \times r_{c} \times C )N_{F} + N_{F}
$$
I neural network libraries we also have the **stride parameter** that tells the filter how much it needs to jump to find the next item. This however will reduce the spatial extent of the filter.

We cannot create a CNN with just the convolutional layers, we also need a non-linear activation function. The most popular is the ReLU  [[Feed Forward Neural Networks#Activation functions]]. On top of that we introduce also **pooling layers** that are used to reduce the spatial size of the volume, so it's a downsampling operation.

>[!note]
>Pooling layers commonly use the $max$ operation in their convolutions. This is called **max-pooling**.

