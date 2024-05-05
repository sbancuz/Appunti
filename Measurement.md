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

An observable $A$ is described by a Hermitian operator $\hat{A}$ -- hence real eigenvalues and orthogonal eigenfunctions -- with the existence of an **orthonormal basis** -- for the Hilbert space $\mathcal H$ -- formed by eigenvalues of $\hat{A}$. This concept can be expanded to the [[Projective quantum measurement]]
### Fidelity

The fidelity between two quantum states $\phi$ and $\psi$ is defined
$$
F(\psi, \phi) = \frac{\left< \psi | \phi \right>\left< \phi | \psi \right>}{\left< \psi | \psi \right> \left< \phi | \phi \right>  } = \frac{\left< \phi | \psi \right>^{*}\left< \phi | \psi \right>}{||\psi||^{2} || \phi||^{2}  } = \frac{|\left< \phi | \psi \right>|^{2}}{||\psi||^{2} || \phi||^{2}  }
$$
This means that we can define the probability density distribution in terms of the fidelity, in fact
$$
P_{n} = F(\psi, \phi_{n})
$$
#### Properties
1) The fidelity is a **real number** $0 \leq f \leq 1$, so it can be seen as a percentage that represents the degree of **similarity** of the quantum states
	This can be proven using the **Cauchy-Schwartz** inequality $|\left< \psi | \phi \right>| \leq||\psi||\times||\phi||$ . The fidelity is $1$ iff the two vectors are linearly independent. This is because you can write $\psi = \alpha \phi$ , this means that they describe the same quantum state. This is because in general a quantum state represents a *ray* in the Hilbert space. Inversely the fidelity is $0$ iff the two quantum states are orthogonal
	This is for the same reason as before. 
	
	We can generalize this notion to $F(\psi, \phi) = \cos^{2}\theta$ with $F(\dots) = 1 \to0 \leq \theta \leq 90^{o} \gets F(\dots) = 0$ 
	
	Being a probability we also have that $\sum_{n}P_{n} = 1$

2) $F(\psi|\phi) = F(\phi|\psi)$
	I can invert the numerator and the result is the same

3)  Fidelity is defined for quantum states, so $F(\alpha \psi, \beta \phi) = F(\psi, \phi)$
$$
F(\alpha \psi, \beta \phi) = \frac{\left< \alpha\psi | \beta\phi \right>\left< \beta\phi | \alpha\psi \right>}{\left< \alpha\psi | \alpha\psi \right> \left< \beta\phi | \beta \phi \right> } = \frac{|\alpha|^{2}|\beta|^{2}|\left< \phi|\psi \right>|^{2} }{|\alpha|^{2}|\beta|^{2}||\psi||^{2} || \phi||^{2}  }
$$
### Discrete spectrum observable continuation

A discrete spectrum is such that we have a **countable** infinite of eigenfunctions $\phi$ and associated eigenvalues $\lambda$. We now consider a **discrete spectrum** observable $A$ for the Hilbert space $L^{2}$ of normalizable wave function, which for example are the
- orbital angular momentum
- the spin considered to the [[qubit]]
- energy

We can define the expansion of a wave function in eigenfunctions of a discrete spectrum observable as
$$
\psi = \sum\lambda_{n}\phi_{n} \qquad \lambda_{n} = \left< \phi_{n} | \psi \right> \qquad ||\psi||^{2} = \sum |\lambda_{n}|^{2} 
$$
 We can also define the expectation value for a discrete spectrum observable as
$$
\left< A \right>_{\phi} = \frac{\left<  \psi | \hat{A}\psi \right> }{\left< \psi | \psi \right> } = \text{normalized} = \left<  \psi | \hat{A}\psi \right>  
$$
This can be demonstrated by first setting $\psi = \sum_{n}\lambda_{n} \phi_{n}$ where $\phi_{n}$ is an orthonormal basis formed by the eigenstates of $\hat{A}$. So
$$
\begin{align}
\left< \psi | \hat{A}\psi \right>  & = \int _{-\infty}^{\infty}\psi^{*}\hat{A}\sum\lambda_{n}\phi_{n}(\bar{r}) \, d\bar{r}  =\sum a_{n}\lambda_{n} \int _{-\infty}^{\infty}\psi^{*}\phi_{n}(\bar{r}) \, d\bar{r}   =\sum a_{n}\lambda_{n} \int _{-\infty}^{\infty}\sum \phi_{m}^{*}\lambda_{m}^{*} \phi_{n}(\bar{r}) \, d\bar{r} = \\
	 & =\sum\sum\lambda_{n}\lambda_{m}^{*}a_{n} \int _{-\infty}^{\infty}\phi_{n}(\bar{r})\phi_{m}^{*}(\bar{r}) \, d\bar{r} =\sum\sum\lambda_{n}\lambda_{m}^{*}a_{n} \delta_{mn} = \sum |\lambda|^{2}a_{n} = \sum a_{n} |\left< \phi_{n} | \psi \right> | ^{2} = \\
 &  =\sum a_{n} F(\phi_{n}, \psi) = \sum a_{n}P_{n} 
\end{align}
$$

The uncertainty in the measurement $\Delta_{\psi} A$ as
$$
\begin{align}
(\Delta A)^{2}_{\psi}  & = \left< (A - \left< A \right>_{\psi})^{2} \right>_{\psi} =  \left< A^{2} - 2A\left< A \right>_{\psi} + \left< A \right>_{\psi}^{2}   \right>_{\psi} = \left< A^{2} \right>_{\psi} -2\left< A \right>_{\psi}\left< A \right>_{\psi} + \left< A \right>^{2}_{\psi} = \left< A^{2} \right>_{\psi} - \left< A \right>_{\psi}^{2}      

\end{align}
$$
### Continuous spectrum observable

The real eigenvalues of $A$ form a continuum and are indexed by a continuous parameter $\alpha \in I$. The generalized orthogonal condition in the continuous case becomes
$$
\left< \phi_{\alpha} | \phi_{\beta} \right> = \delta(\alpha - \beta) = \begin{cases}
\infty  & \alpha = \beta\\
0  & \alpha \neq\beta
\end{cases} 
$$
In the continuous superposition can be rewritten as
$$
\psi = \int _{-\infty}^{\infty}\lambda_{\alpha}\phi_{\alpha} \, d\alpha  \qquad ||\psi|| = 1
$$
The relation with the eigenfunction remains
$$
\hat{A} \phi_{\alpha} = a_{\alpha}\phi_{a}
$$
and in the non-degenerate case we can say
$$
\alpha = a_{\alpha}
$$
This means that
$$
\lambda_{\alpha} = \left< \phi_{\alpha} | \psi \right>  \qquad \int _{I} |\lambda_{\alpha}|^{2} \, d\alpha = 1 \qquad P(\alpha) = |\left< \phi_{\alpha} | \psi \right> | ^{2} = |\lambda_{\alpha}|^{2} 
$$
### Simultaneously measurable observable

Two observable are said to be simultaneously measurable or **compatible** when it exists an orthonormal basis formed by **common eigenstates** of both Hermitian operators $\hat{A},\hat{B}$. This condition can be defined as: two observable $A.B$ are compatible iff $\hat{A},\hat{B}$ commutate

