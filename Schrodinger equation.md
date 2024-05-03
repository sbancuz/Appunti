---
tags:
  - quantum
---
The Schrodinger equation describes the evolution of a **well-defined quantum state** of a single quantum particle over time up to some [[Measurement]] where the wave function will collapse onto a quantum state defined by the plain wave.

We know that in the [[Position representation#Position representation]] for a quantum system consisting of a single particle the momentum component is
$$
\hat{p}_{x} = -i \hbar \frac{\delta}{\delta x} \qquad\hat{p}_{y} = -i \hbar \frac{\delta}{\delta y} \qquad\hat{p}_{z} = -i \hbar \frac{\delta}{\delta z} \qquad
$$
Quantum states with well-defined momentum for this system are described by the [[Wave function]].
$$
\psi(\bar{r}) = C e^{i \bar{k} \times \bar{r}} = C e^{i/\hbar \bar{p}\times \bar{r}}
$$
Now we consider a **free particle** -- no external forces are applied. We also consider the plain waves to have a **well-defined total energy**.
$$
E_{tot} = E_{kin} + \cancel{E_{pot}} = \frac{1}{2}m v^{2} = \frac{1}{2} \frac{p^{2}}{m}
$$
The plain waves are also eigenfunctions of the observable $E_{tot}$ described by the **Hamiltonian operator** $\hat{H}$. For a free particle we have
$$
\hat{H}^{free} = \frac{\hat{\bar{p}}^{2}}{2m} \to \text{position representation} \to \hat{H}^{fre e}= \frac{(-i \hbar )^{2}}{2m}\underbrace{ \left( \frac{\delta^{2}}{\delta \bar{r}} \right) }_{  \text{Laplace op}} ={(-i \hbar )^{2}}{2m}\triangledown^{2} 
$$
So putting it all together for a generic quantum state
$$
\hat{H}^{\text{free}} \psi(\bar{r}) =-\frac{ \hbar^{2} }{2m}\triangledown^{2} \psi(\bar{r})
$$
In quantum physics **any quantum state** with well-defined energy $E$ is **monochromatic**, that is, it presents well defined frequency.
$$
E = h \nu
$$
So now we have to add the time domain to our plain wave equation
$$
\psi_{E} (\bar{r}, t) = C e^{i \bar{k} \times \bar{r}} e^{-i \omega t} =C e^{i/\hbar (\bar{p} \times \bar{r}-E t)}  = \psi_{E}(\bar{r})e^{-i E/\hbar}
$$
The last step to obtain the Schrodinger equation is to derive with respect to time
$$
\frac{ \partial  }{ \partial t } \psi_{E}(\bar{r}, t) = -i \frac{E}{\hbar}\psi_{E}(\bar{r}, t)
$$
and write using the Hamiltonian we can write the equation for the position representation
$$
\frac{ \partial  }{ \partial t } \psi_{E}(\bar{r}, t) = -i \frac{1}{\hbar} \hat{H}\psi_{E}(\bar{r}, t)
$$
>[!note]
>The Schrodinger equation works even with **non-free** particles. This is just a *guess* but it works.

So we can write another representation of this equation for a general quantum state
$$
\frac{d}{dt} \psi(t) = - \frac{i}{\hbar} \hat{H} \psi(t) \qquad \hat{H} \psi(t) = i\hbar \frac{d}{dt} \psi(t)
$$
### The Hamiltonian operator

In the non-relativistic quantum mechanics for a single particle
$$
\hat{ H} = f(\hat{\bar{r}}, \hat{\bar{p}}, t)
$$
