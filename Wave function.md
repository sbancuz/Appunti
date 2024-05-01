---
tags:
  - quantum
---
A wave function for an electron, or in general any particle, with well-defined velocity, or in the case of quantum physics the momentum since
$$
\bar{p} = m\bar{v}
$$
this wave function is also a **plain wave**. This is also in agreement with the theories of the [[De Broglie wavelength]]. 

We can define the wave function for a single electron as such
$$
\psi(\bar{k}) = Ae^{i\phi}e^{i\bar{k} \times \bar{r}}
$$
>[!tip]
>In most quantum systems we can set the first term to $1$

The states of a well-defined value of an observable $M$ are the eigenvalues of an Hermitian operator $\hat{M}$ associated. The corresponding eigenvalue is the well-defined value of the observable.

>[!note]
>The eigenvalues of an Hermitian operator are real

This operators can be defined as follows
$$
\hat{p}_{x} = -i\hbar \frac{\delta}{\delta x} \qquad\hat{p}_{y} = -i\hbar \frac{\delta}{\delta y} \qquad\hat{p}_{z} = -i\hbar \frac{\delta}{\delta z} \qquad
$$
Or more compact
$$
\hat{p} = -i\hbar \triangledown 
$$
### Dirac representation

The **scalar product** of the wave function is defined in **bra-ket** notation as 
$$
\left< \psi_{1}(\bar{r}) | \psi_{2}(\bar{r}) \right>  \equiv \iiint _{-\infty}^{\infty}\psi_{1}^{*}(\bar{r})\psi_{2}(\bar{r}) \ dxdydz
$$
The **norm** of a wave function is defined as 
$$
||\psi(\bar{r})||^{2} = \left< \psi(\bar{r}) | \psi(\bar{r})\right>  \geq 0 \qquad \text{iff } ||\psi|| =0
$$

The **normalized wave function** is given by
$$
\psi'(x,y,z) = \frac{\psi(x,y,z)}{||\psi||}
$$
This also means that 
$$
|| \psi'||^{2} = \left< \psi',\psi' \right> = 1 
$$
### Position representation

Consider a wave function with well-defined **momentum** $\bar{p}'=\hbar \bar{k}'$. The wave function is an **eigenfunction** of an hermitian operator $\hat{\bar{p}}$. Then the complementary representation in position representation defined 
$$
\psi_{\bar{p}}(\bar{r}) = A_{0}e^{i\phi_{0}}e^{i\bar{k}'\times \bar{r}} \qquad \hat{p_{y}} \psi_{\bar{p}'}(\bar{r}) -= -i \hbar \frac{\delta}{\delta y}Ce^{i\bar{k}\times \bar{r}} = -i^{2}\hbar \bar{k_{y}'}e^{i\bar{k}\times \bar{r}}
$$
The norm of this representation is given by
$$
||\psi_{\bar{p}'}||^{2} = \iiint _{-\infty}^{\infty}|\psi_{\bar{p}'}(\bar{r})|^{2} \ dxdydz = |C|^{2}\iiint_{-\infty}^{\infty}  \ dxdydz = \infty
$$
Since this is clearly unfeasible to calculate we have to truncate the plain wave volume so that the volume will be a finite value. This is also a consequence of the [[Criterion of reality#Heisenberg principle of indetermination]] since we know already the momentum and thus can't know the position. When in this state we can say that the quantum particle is in a **superposition** -- i.e. it has a probability of being in a given position.
$$
\Delta x \approx \frac{\hbar}{\Delta p_{x}}
$$
In fact the square modulus represents the probability density distribution of the measurement at position $\bar{r}$. To find this approximation we can use the expected value over the probability distribution of the measured values for an initial $\psi(x,y,z)$
$$
\left< x \right> = \frac{\iiint _{-\infty}^{\infty}|\psi(x,y,z)|^{2}x \ dxdydz}{\iiint _{-\infty}^{\infty}|\psi(x,y,z)|^{2} \ dxdydz} = \frac{\int _{\infty}^{\infty}x \, dx }{\int _{-\infty}^{\infty} \, dx }=\lim_{ a \to \infty } \frac{\int _{-a/2}^{a/2}x \, dx }{\int _{-a/2}^{a/2} \, dx} = \lim_{ a \to \infty } {\frac{0}{a}} = 0
$$
The variance, that measures the uncertainty we can consider
$$
\left< (x - \left< x \right>)^{2}  \right> = \left< x^{2}  \right>  =\frac{\int _{\infty}^{\infty}x^{2} \, dx }{\int _{-\infty}^{\infty} \, dx }=\lim_{ a \to \infty } \frac{2\int _{0}^{a/2}x^{2} \, dx }{\int _{-a/2}^{a/2} \, dx} = \lim_{ a \to \infty } {\frac{2\left[ \frac{x^{3}}{3} \right]^{a/2}_{0}}{a}} = \lim_{ a \to \infty } {}\frac{a^{3}}{a} = \infty
$$
When considering a [[Measurement#Continuous spectrum observable]] the position operator $\hat{x}$
$$
\hat{x}\phi_{x'} = x'\phi_{x'}
$$
is no more than the 
$$
\phi_{x'}(x) = \delta(x - x')
$$
So the probability density function becomes
$$
P(x) = | \psi (x)| ^{2}
$$

### Delta of Dirac

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
### Momentum representation

Given a well defined quantum state $\bar{r}'$, we can define the Fourier transform 
$$
\mathcal F \{ \delta(\bar{r} - \bar{r}') \} =  e^{-i 2\pi \bar{r}' \times \bar{f}}
$$
where the $\bar{f}$ is defined as
$$
\bar{f} = \frac{\bar{p}}{2\pi \hbar} = \frac{\bar{p}}{h}
$$
This means that by applying the [[Fourier transform]] to the delta of Dirac can transform a position representation of a quantum state to the momentum one. So more formally
$$
\dot{\phi}(\bar{r}) = \left( \frac{1}{\sqrt{ h }} \right)^{3}\mathcal  F \{ \phi(\bar{r}) \} |_{\bar{f} = \bar{p} /h}  = h^{-3/2}\Phi\left( \frac{\bar{p}}{h} \right) = h^{-3/2} \iiint _{-\infty}^{\infty}\phi(\bar{r}) e^{-i/\hbar \bar{r} \times \bar{p}} \ dxdydz
$$
