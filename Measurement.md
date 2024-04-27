---
tags:
  - quantum
---
A quantum measurement of an **observable** -- a property of a quantum particle -- is described as an orthogonal projection into the quantum state with projection coefficient value of $M$. This measurement is performed onto a [[Wave function]].

We can define the probability of finding the particle we want to measure in a *cube* -- this is due to accuracy -- of coordinates $z,y,z$ as
$$
\mathcal P_{\det} =\frac{\iiint_{V_{cube}} |\psi(x,y,z)|^{2}  \ dxdydz}{\iiint_{-\infty}^{\infty} |\psi(x,y,z)|^{2}\ dxdydz} \approx \frac{|\psi(x,y,z)|^{2}\Delta x\Delta y\Delta z}{\iiint_{-\infty}^{\infty} |\psi(x,y,z)|^{2}\ dxdydz} \qquad \text{For deltas $\to$ 0}
$$
The probability density function of measuring the position $\bar{r}$ of a particle is 
$$
\mathcal P_{pos} (x_{p},y_{p},z_{p}) = \lim_{ V \to 0 } \frac{{\mathcal P_{\det}}}{V} = \frac{|\psi(x,y,z)|^{2}}{\iiint_{-\infty}^{\infty} |\psi(x,y,z)|^{2}\ dxdydz} \qquad
$$
and the total probability 
$$
\mathcal P_{tot} = \iiint_{-\infty}^{\infty}\mathcal P_{pos}(x,y,z)  \ dxdydz = 1
$$
The physically realizable quantum states for a particle are described by a normalizable [[Wave function]] -- square modulus integrable.

An observable $A$ is described by a Hermitian operator $\hat{A}$ -- hence real eigenvalues and orthogonal eigenfunctions --  