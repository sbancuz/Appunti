---
tags:
  - quantum
---
Since we can't define a point for a quantum particle to be, we have to use a differential notation to define it's position. Dirac proposed this operator defined as
$$
\psi_{\bar{r}'} (\bar{r}) =\delta(\bar{r} - \bar{r}') = \begin{cases}
\infty  & \bar{r} = \bar{r}' \\
0  & \text{otherwise}
\end{cases}
$$
This is also called a **generalized function**, they are also called **distribution**.

>[!note]
>This is a 3 dimensional delta, it can be rewritten with 1 dimension and it will still behave the same

The definition of this delta function is given by
$$
\int _{-\infty}^{\infty}\delta(x-x') \psi(x)\, dx = \psi(x'), \qquad \psi(x) \text{ is a test function}
$$
This is an example of a **tempered distribution** -- it can be used with a [[Fourier transform]]. Also this test function must tend rapidly to $0$, i.e. an exponential decay and all the derivatives must be continuous. These are called **Schwartz** functions. 

All tempered distributions are the **continuous linear functional** $\phi$ on $\mathcal S$
$$
\phi:\mathcal S \to \mathbb  C \qquad \phi = \delta(x-x') \qquad \left< \delta(x-x')| \psi '\in \mathcal S\right> =  \int _{-\infty}^{\infty}\delta(x-x') \psi(x)\, dx = \psi(x') 
$$
Another important property of this function is that is not normalizable in fact
$$
||\delta(\bar{r}-\bar{r}')||^{2 } = \iiint _{-\infty}^{\infty}\delta(\bar{r}-\bar{r}') \delta(\bar{r}-\bar{r}') \ dxdydz = \delta(0) = \infty
$$
																	^^ *test function,*