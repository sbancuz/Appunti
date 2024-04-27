---
tags:
  - quantum
---
In 1924 De Broglie extended the [[Particle-wave dualism]] found for the radiation also to matter. So for each microscopic particle there is an associated **matter wave** of wavelength
$$
\lambda = \frac{h}{p} = \frac{h}{mv}
$$
where $p$ is the momentum of a non relativistic motion. So we can rewrite this as
$$
p = \frac{h}{\lambda} = \frac{h}{2\pi}k = \hbar k = mv
$$
### Diffraction of the electrons

According to the De Broglie wavelength it has been verified by Davisson-Germer considering the diffraction of an electron beam in a nickel crystal. Using a cathode ray tube it's possible to generate a **collimated beam of electrons** with **well-defined** kinetic energy and velocity

![[CRT.png]]  

$$
E_{kin} = eV_{a} = \frac{1}{2}mv^{2} = \frac{p^{2}}{2m} \qquad p = \sqrt{ 2m E_{kin} } = \sqrt{ 2meV_{a} }
$$
A matter **plane wave** with wave vector $k$ is associated with the electron beam
$$
k = \frac{p}{\hbar} \qquad\lambda =\frac{2\pi}{k} = \frac{h}{p} = \frac{h}{\sqrt{ 2meV_{a} }}
$$
Well defined in the context of quantum physics means that some property of a quantum particles behaves in a deterministic way, as if it were in a normal setting. A non-obvious implication of this is that if an **observable** is well defined, then we can make a [[Measurement]] it as many times as we want and we will still get the same result.
### Single slit diffraction

It's also possible to apply the matter wave calculations to the Fraunhofer diffraction patterns of optics. In this case the beam comes from a slit of width $D$ and the intensity of the energy at distance $L$ is given by
$$
I(x)= sinc^{2} \left( \frac{Dx}{\lambda L} \right)
$$
that has a zero in $x = m \frac{\lambda L}{D}$ where $m$ is a non-zero integer.