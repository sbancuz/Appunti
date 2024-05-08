---
tags:
  - quantum
---
The qubit is the fundamental entity of quantum information, computation and communication theory. They represent the quantum states of a two state quantum system. This means that they are described by a two dimension Hilbert space, so they are a bi-dimensional vectors.

In a two dimensional orthonormal basis $\{ \phi_{0},\phi_{1} \}$
$$
\psi = \alpha \phi_{0} + \beta\phi_{1}
$$
>[!note]
>A polarized single [[Photon]] can represent a qbit using its horizontal and vertical waves

We can use [[Wave function#Dirac representation]] to write the states of a qbit.
$$
\ket{\psi} = \sum \lambda \ket{\phi} \text{ where } \ket{\phi_{n}} = [0 \dots \underbrace{ 1 }_{ \text{nth-pos} } \dots 0]^{T}   
$$
In the case of qubits we just have
$$
\ket{\psi}  = \alpha \ket{\phi_{0}} + \beta \ket{\phi_{1}} = \alpha \ket{0}  + \beta \ket{1}  
$$
There is also a **dual** representation
$$
\bra{\psi}  = \sum \lambda^{*} \bra{\phi} 
$$
that can be calculated from the **bra** notation using an anti-linear isometric operator $+$, or vice versa $+^{-1}$, this is called the **Daga** and mathematically is the conjugate transposition.
$$
\bra{\psi}  = \ket{\psi} ^{+}
$$
### Norm 

We can define the norm for a qubit as
$$
||\psi||^{2} = |\alpha|^{2} + |\beta|^{2} 
$$
