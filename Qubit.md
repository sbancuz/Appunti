---
tags:
  - quantum
---
The qubit is the fundamental entity of quantum information, computation and communication theory. They represent the quantum states of a two state quantum system. This means that they are described by a two dimension Hilbert space, so they are a bi-dimensional vectors.

They can also be represented with a [[Bloch sphere]]. It's important to note that, to making a quantum computer, we need to have **coherent superpositions** -- $\alpha.\beta$ are stable coefficients, thus they only change in a controlled way, not randomly.

In a two dimensional orthonormal basis $\{ \phi_{0},\phi_{1} \}$
$$
\psi = \alpha \phi_{0} + \beta\phi_{1} \in \mathcal  H
$$
>[!note]
>A polarized single [[Photon]] can represent a qbit using its horizontal and vertical waves

We can use [[Wave function#Dirac representation]] to write the states of a qbit.
$$
\ket{\psi} = \sum \lambda \ket{\phi} \text{ where } \ket{\phi_{n}} = [0 \dots \underbrace{ 1 }_{ \text{nth-pos} } \dots 0]^{T}   \in \mathcal  H_{ke t} = \mathcal  H
$$
In the case of qubits we just have
$$
\ket{\psi}  = \alpha \ket{\phi_{0}} + \beta \ket{\phi_{1}} = \alpha \ket{0}  + \beta \ket{1}  
$$
There is also a **dual** representation
$$ 
\bra{\psi}  = \sum \lambda^{*} \bra{\phi_{n}}   \text{ where } \bra{\phi_{n}} =  [0 \dots \underbrace{ 1 }_{ \text{nth-pos} } \dots 0] \in \mathcal  H_{b ra} = \mathcal H^{*}
$$
that can be calculated from the **bra** notation using an anti-linear isometric operator $+$, or vice versa $+^{-1}$, this is called the **Daga** and mathematically is the conjugate transposition.
$$
\bra{\psi}  = \ket{\psi} ^{+}
$$
>[!important]
>The bra represents a functional, meanwhile the ket represents a vector. But is also true that a functional is also a vector, but you have to take the conjugate
### Norm 

We can define the norm for a qubit as
$$
||\psi||^{2} = |\alpha|^{2} + |\beta|^{2} 
$$
If $||\psi||^{2} = 1$ we can say that the qubit is **normalized**. 
### Computational basis

To represent a quantum state we need to have that the eigenfunctions of state to be **orthonormal**. So for a qubit a this basis can be written as
$$
\{ \ket{\phi_{1}} , \ket{\phi_{2}}  \} \in \mathcal H_{2}^{ke t}
$$
For simplicity, we can just write 
$$
\{  \ket{0} , \ket{1}  \} \in \mathcal  H_{2}^{ke t}
$$
This means that the quantum state can be written as
$$
\ket{\psi}  = \alpha \ket{0}  + \beta \ket{1} \to \left[\begin{matrix}
\alpha \\
\beta
\end{matrix}  \right]  \text{ or } \bra{\psi}  = \alpha^{*}\bra{0}  + \beta^{*}\bra{1} \to \left[ \alpha^{*}  \\ \beta^{*}\right]  
$$
We can also define some common vectors to better ease our notation
$$
\ket{0}  = \left[ \begin{matrix} 1\\ 0 \end{matrix} \right] \quad (H)\qquad 

\ket{1}  = \left[ \begin{matrix} 0\\ 1 \end{matrix} \right]  \quad (V)
$$
If we consider a **diagonal state of polarization** -- so it's in a superposition and it has both $H$ and $V$ components -- we can have
$$
Q = \frac{1}{\sqrt{ 2 }} (H + V)
$$
Then we can also define some other common vectors
$$
\ket{ + }= \frac{1}{\sqrt{ 2 }} (\ket{0}  + \ket{1} ) = \frac{1}{\sqrt{ 2 }} \left[ \begin{matrix} 1\\ 1 \end{matrix} \right]
\qquad
\ket{ - }= \frac{1}{\sqrt{ 2 }} (\ket{0}  - \ket{1} ) = \frac{1}{\sqrt{ 2 }} \left[ \begin{matrix} 1\\ -1 \end{matrix} \right]
$$ There is also the **circular state of polarization**
$$
L = \frac{1}{\sqrt{ 2 }} (H - V)
$$
that uses
$$
\ket{ i }= \frac{1}{\sqrt{ 2 }} (\ket{0}  + i \ket{1} ) = \frac{1}{\sqrt{ 2 }} \left[ \begin{matrix} 1\\ i \end{matrix} \right]
\qquad
\ket{- i }= \frac{1}{\sqrt{ 2 }} (\ket{0}  - i \ket{1} ) = \frac{1}{\sqrt{ 2 }} \left[ \begin{matrix} 1\\ -i \end{matrix} \right]
$$
>[!warning]
>Careful when using the bra notation since here we have to calculate the complex conjugate, so $i$ becomes $-i$

Since the quantum state is normalized, we can also write the coefficients $\alpha,\beta$ as
$$
\alpha = \cos\left( \frac{\theta}{2} \right) e^{i\phi_{0}} \qquad\beta=\sin\left( \frac{\theta}{2} \right) e^{i\phi_{1}}
$$
Then the quantum state can be rewritten as
$$
\ket{\psi}  = \cos\left( \frac{\theta}{2} \right) e^{i\phi_{0}} \ket{0} +  \sin\left( \frac{\theta}{2} \right) e^{i\phi_{1}}\ket{1} = e^{i \phi_{0}}\left[\cos\left( \frac{\theta}{2} \right) \ket{0} +  \sin\left( \frac{\theta}{2} \right) e^{i(\phi_{1} -\phi_{0})}\ket{1}  \right]  \underbrace{ \to }_{ \phi_{0} = 0, \alpha \text{ real} } \left[ \begin{matrix}
\cos \left( \frac{\phi}{2} \right) \\
\sin \left( \frac{\phi}{2} \right) e ^{i\phi}
\end{matrix} \right] 
$$


