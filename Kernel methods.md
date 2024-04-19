---
tags:
  - machine_learning
---
Many linear parametric models can be recast into equivalent **dual representations** where predictions are based on the **kernel function** evaluated at the samples. 

Kernel methods don't scale well with a lot of data, in fact unlike [[Supervised learning]] methods they scale with the number of samples. General techniques for [[Machine learning]] scale with parameters, so they work better when making prediction with a lot of data. Unlike parametric method like [[Regression]], kernel methods are memory based. This means that after you train your kernel, you still need the data to compute the result.

They come from the need in the 90's of **capturing nonlinear patterns** in some data and allow us to work in a high number of dimension of features, in fact you can make a kernel with an infinite amount of features.

Nowadays kernel methods allow linear models to work in nonlinear settings by **mapping data to higher dimensions** where they exhibit linear patterns. These mappings are basically free!!
### Feature mapping

Consider the following mappings $\phi$ for an example $x = \{ x_{1},\dots,x_{M} \}$
$$
\phi:x\to \{ x_{1}^{2},\dots,x_{M}^{2},x_{1}x_{2},\dots,x_{M-1}x_{M} \}
$$
This is an example of a **quadratic mapping**, this clearly leads to an extremely high number of features. Thankfully kernels allow us to use these kind of mappings without explicitly computing them. Take the kernel function
$$
k(x,x') = \phi(x)^{T}\phi(x')
$$
where the $\phi$ is a fixed nonlinear mapping or **basis function**. This representation still uses the mapping, but it's just for notation. They won't be used.

>[!tip]
>A kernel function is **symmetric** with its arguments.

A **stationary kernel** is defined as $k(x,x')=k(x-x')$ and **homogeneous kernels** are $k(x,x')= k(||x-x'||)$

For every kernel we can define the **Gram matrix** $K=\Phi \times\Phi^{T}$ an $N \times N$ matrix with elements
$$
K_{nm}=\phi(x_{n})^{T}\phi(x_{m})=k(x_{n},x_{m})
$$
And the matrix is defined as the matrix of all inner products
$$
K = \left[\begin{matrix}
k(x_{1},x_{1})  & \dots  & k(x_{1},x_{N}) \\
\vdots  & \ddots  & \vdots \\
k(x_{N},x_{1} & \dots  & k(x_{N},x_{N})
\end{matrix}\right]
$$
### Constructing kernels

First we have the naive case were we can find a mapping directly then you are done. So you need to find a
$$
k(x,x') = \phi(x)^{T}\phi(x') = \sum \phi_{i}(x)^{T}\phi _{i}(x')
$$
where $\phi$ are valid basis functions. Consider the kernel function 
$$ 
k(x,z)=(x^{T}z)^{2} =(x_{1}^{2},\sqrt{ 2 }x_{1}x_{2},x_{2}^{2})(z_{1}^{2},\sqrt{ 2 }z_{1}z_{2},z_{2}^{2})^{T} = \phi(x)^{T}\phi(z)
$$
We can generalize this result to $(x^{T}z + c)^{p}$ that represents all the terms of a polynomial up to degree $p$
In case we can't find this construction directly we use the **Mercer's theorem** to construct one. It states:
Any continuous, symmetric, positive semi-definite kernel function $k(x,y)$ can be expressed as a **dot product** in a high dimension space. The idea is that new kernels can be constructed by some other known kernel.

![[kernels.png]]

