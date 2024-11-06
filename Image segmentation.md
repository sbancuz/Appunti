---
tags:
  - neural_networks
---
Given an image $I\in \mathbb R^{R\times C \times 3}$ having a domain $\mathcal X$, the goal of image segmentation is estimating a partition $\{ R_{i} \}$ such that
$$
\bigcup_{i}R_{i} = \mathcal  X, \qquad R_{i} \cap R_{j} = \emptyset
$$
This is basically [[Clustering]], but with the difference that we are looking to associate each pixel of an image to a label. To achieve this we can start form the same techniques that we use for [[Image classification]] and apply a [[Convolutional Neural Network]].

>[!note]
What if I just use convolution for image segmentation? I can put some activation and convolutional layers, ending with an *argmax*  activation function. And that kinda works, it's slow, inaccurate and very inefficient though. This is because this way it has a very small receptive field.
>
>The reason this is so inefficient is that we have to both **go deeper** to extract high level information and stay local to **not lose spatial resolution**. So the solution to this dilemma is to combine **fine** and **coarse** layers to the model.

So the idea is to put both down and up sampling layers to convey both types of information.

![[image segmentation.png]]

So the first half will perform a **classification** step, then the second half will up sample the image to provide the most amount of spatial information possible. Of course this doesn't come without some loss, but it still works.

>[!note] Up-sampling
>To perform up-sampling we have a few methods:
>- nearest neighbor $\to$ copy the value of the original pixel to the new ones
>- bed of nails $\to$ only copy the original to one pixel of the new image 
>
>To make this process learnable we have to apply **transpose convolutions**, so convolutions where the outputs overlap.




