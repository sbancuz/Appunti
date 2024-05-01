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