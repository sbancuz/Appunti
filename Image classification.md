---
tags:
  - neural_networks
---
Digital images in memory are represented -- if they are not compressed that is -- as matrices of pixel
$$
I \in \mathbb R^{Rows\times Cols\times_{3}}
$$
![[Column wise unfolding.png]]

Where the $3$ is given by the number of **color channels** of an image. Since all the colors can be created from the $3$ primary colors, we can store an image as the combination of the images only containing that color.

The most important operation when dealing with images is a transformation that mixes all the pixels locally around the neighborhood $U$ of a given pixel
$$
G(r,c) = T_{U}[I](r,c)
$$
Where $I$ is the image, $G$ the output, $U$ the neighborhood and $T_{U}: \mathbb R^{3} \to \mathbb R^{3}$ a space invariant transformation. When the output is a linear combination of the input then it's called a **linear transformation**.

![[Spatial filter.png]]

>[!note]
>The dashed square is the region $(u-r, v-c) \in U$

We can define the **correlation** among a fileter $w = \{ w_{ij} \}$ and an image as
$$
(I \otimes w)(r,c) = \sum^{L}_{u = -L}\sum^{L}_{v = -L}\underbrace{ w(u,v) }_{ \text{Kernel} } * I(r+u,c+v)
$$
Let's say we try to use a $1$ layer [[Feed Forward Neural Networks]] to classify images, the number of inputs is given by 
$$
d = R \times C \times 3
$$
>[!example]
For example we use the CIFAR-$10$ dataset to classify over. Then we have
>
>```c
>Layer (type) Output Shape Param #
>=================================================================
>Input (InputLayer) [(None, 32, 32, 3)] 0
>_________________________________________________________________
>Flatten (Flatten) (None, 3072) 0
>_________________________________________________________________
>Output (Dense) (None, 10) 30730
>=================================================================
>Total params: 30,730
>Trainable params: 30,730
>Non-trainable params: 0
>```
>
>which is already has a lot of parameters. If we want to add an hidden layer having half of the neurons and fully connect with the previous one we would have
>$$
\underbrace{ 3072 }_{ \text{First layer} } \times \underbrace{ 1536 }_{ \text{Second layer} } \times \underbrace{ 10 }_{ \text{Output layer} } = 4.720.128 \text{ parameters!}
>$$
>which is obviously too much for such a small network -- note that this only is the layer $0 \to 1$ connection.
>
>An image classifier can be seen as a function that maps an image $I$ to a confidence score for each class of $L$
>$$
\mathcal  K: \mathbb R^{d} \to \mathbb R^{L}
>$$
>where $\mathcal K(I)$ is a $L$-dimensional vector and the i-th component contains a score of how likely $I$ belongs to $i$. So since it's a linear transformation we have
>$$
\mathcal  K(x) = s = Wx + b
>$$
>>[!note]
>>Using non-linear layers, such as activation function is mandatory since stacking linear layers is the same as using one layer which is their combination
>
>However this model that we can't really expand is really too simplistic, it won't ever correctly classify images in general.

This is indeed a very challenging problem since we have to deal with
- dimensionality
- label ambiguity 
	An image could contain multiple things, what do we choose?
- transformation 
	Images can be wildly different, think lighting conditions, deformations, view point, occlusion an many others
- Inner class variability
	Images in the same class might be dramatically different, think of different types of chairs or animals
- Perceptual similarity
	If something is similar to another this is not the same as saying that the pixels are similar