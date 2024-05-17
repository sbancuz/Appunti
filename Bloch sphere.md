---
tags:
  - quantum
---
Consider the [[Qubit]] written in the circular representation. We can visually plot is as a sphere
![[bloch sphere.png]]

This sphere as radius $r = 1$. So we can define a point in the Bloch sphere as
$$
P(\underbrace{ \theta }_{ \text{co-latitude} }, \underbrace{ \phi }_{ longitude }) \quad \text{ with }\quad  \underbrace{ 0 }_{ \text{north-pole} } \leq \theta \leq \underbrace{ \pi }_{ \text{south-pole} } \text{ and } \quad -\pi \leq \phi \leq \pi 
$$
So the point can be defined in terms of
$$
P(\theta, \phi) \to e^{i\phi_{0}}
\left[ \begin{matrix}
\cos \left( \frac{\phi}{2} \right) \\
\sin \left( \frac{\phi}{2} \right) e ^{i\phi}
\end{matrix} \right]  = \left[ \begin{matrix}
\alpha \\
\beta
\end{matrix} \right]
$$
with 
$$
\begin{cases}
\phi = \angle \beta - \angle \alpha \\
\theta = 2\arctan \frac{|\beta|}{|\alpha|} 
\end{cases}
\qquad \text{ given by } \qquad  \frac{|\beta|^{2}}{|\alpha|^{2}} = \tan^{2} \frac{|\theta|}{2} 
$$
If we define $\gamma$ as the angle between two points with respect to the center of the sphere we can define the [[Measurement#Fidelity]] as
$$
F(\psi', \psi'') = |\left< \psi'|\psi'' \right> |^{2} = \cos^{2}\left( \frac{\gamma}{2} \right)
$$
This means that $F= 1$ is when the two points are the same, so $\gamma = 0$, when $F= 0$ it means $\frac{\gamma}{2} = 90$  so $\gamma = \pi$ or visually, the two points are opposite from one another. 

>[!important]
This is general for every point on the Bloch sphere, not only for the *know* ones.
### Bloch vector

Another representation of the [[Qubit]] is the Bloch vector $\bar{u}$
$$
\bar{u}_{p} = (x_{p}, y_{p}, z_{p})
$$
which is just the Cartesian representation of a point in a Bloch sphere.
$$
\bar{u} =\begin{cases}
x_{p} = \sin \theta \cos \phi\\
y_{p} = \sin \theta \sin \theta\\
z_{p} = \cos \theta
\end{cases}
$$

