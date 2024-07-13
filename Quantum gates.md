---
tags:
  - quantum
---
Quantum gates are the equivalent of the normal logic gates, but for quantum computers that operate on [[Qubit]]. In quantum communications the only gates used are the **single-qubit quantum gates**. 
$$
\psi_{in} \to \text{Gate} \to \psi_{out}
$$
Quantum gates implement **deterministic, reversible, linear operations and preserves scalar products** on qubits. So
$$
\hat{U} \hat{U}^{+} = \hat{I} \quad \text{ with } \quad \hat{U} ^{+} = \hat{U}^{-1}
$$
A linear operator in a given orthonormal basis is represented by a $D\times D$ matrix acting on vectors -- i.e. the quantum states. So
$$
\ket{\psi_{out}}  = \hat{U}(\alpha \ket{0} + \beta \ket{1} ) = \alpha \hat{U}\ket{0}  + \beta \hat{U}\ket{1} 
$$
So to compute the general quantum state we just need to know how the operator operates on these two states. So we get that
$$
\left[ \begin{matrix}
\alpha_{out} \\ \beta_{out}
\end{matrix} \right] = \left[ \begin{matrix}
\alpha_{in} \left< 0 | \hat{U} | 0 \right> + \beta_{in} \left< 0 | \hat{U} | 1 \right> \\
\alpha_{in} \left< 1 | \hat{U} | 0\right>   + \beta_{in} \left< 1 | \hat{U} | 1 \right> 
\end{matrix} \right]  
$$
So the linear operator can be written as
$$
\hat{U} \to \left[ \begin{matrix}
\left< 0 | \hat{U} | 0 \right>  &  \left< 0 | \hat{U} | 1 \right> \\
 \left< 1 | \hat{U} | 0\right>    &  \left< 1 | \hat{U} | 1 \right> 
\end{matrix} \right]  = \left[ \begin{matrix}
u_{00} &  u_{01} \\
 u_{10}   & u_{11}
\end{matrix} \right]  
$$
This means that the application of a linear operator to a ket, it's just the matrix multiplication.
$$
\ket{\psi_{out}}  = \hat{U} \ket{\psi_{in}}  
$$
### Adjoint operator

Before defining the adjoint operator we first need to define the **dual operator** $\hat{A}^{\text{dual}} = \hat{A}^{+}$. This leads to 
$$
\braket{ \cdot}A^{dual} \equiv \bra{\cdot}\hat{A}^{+} \to  (\hat{A}  \ket{\psi_{in}}  )^{+} \equiv \ket{\psi_{out}} \to \bra{\psi_{out}}  \equiv \bra{\psi_{in}} \hat{A}^{+} 
$$
Where the matrix $A^{+}$ is just the transposed conjugate matrix of $A$. Now we consider a linear operator $\hat{A}$ in a finite-dimension Hilbert space, we can now represent $\hat{A}$ in a given orthonormal basis $\{ \ket{\phi_{n}} \}$ by a square matrix with complex coefficients where
$$
a_{mn} = \left< \phi_{m} | \hat{A} | \phi _{n} \right> 
$$
This action is represented as a simple matrix multiplication. We can define now the adjoint operator as
$$
\hat{A}^{adj}\ket{\cdot} \equiv \hat{A}^{+} \ket{\cdot} \to \hat{A}^{+}\ket{\psi'} \equiv \ket{\psi''}  
$$
A unitary operator $\hat{U}$ is represented in an orthonormal basis by a **unitary matrix** $U$ -- a matrix with orthonormal rows and columns
$$
U^{-1} = U ^{+} = \left[ \begin{matrix}
u_{00}^{*}  & u_{10}^{*}   \\
u_{01}^{*}    & u_{11}^{*}  
\end{matrix} \right] \qquad \begin{cases}
|u_{00}|^{2}  + |u_{10}|^{2} = 1 \\
|u_{01}|^{2} + |u_{11}|^{2} = 1
\end{cases} \qquad u_{00}^{*}u_{01} + u_{10}^{*}u_{11} = 0
$$
>[!note]
This means that a unary operator is a $1$ to $1$ mapping between orthonormal basis
### Quantum not gate

The quantum not gate, or x-Pauli gate is 
$$
\ket{ 0} \xrightarrow{\hat{x}}\ket{1} \qquad \ket{1}  \xrightarrow{\hat{x}}\ket{0}  
$$
So $\hat{x}$ is represented by the computational basis by the anti-diagonal matrix, more precisely is the **anti-identity matrix**
$$
X = \left[ \begin{matrix}
0  & 1 \\
1  & 0
\end{matrix} \right] 
$$
We also have that
$$
\hat{x}\ket{+} = \ket{+}  \qquad \hat{x}\ket{-} = \ket{-}  
$$
So both the $\ket{-}$ and $\ket{+}$ are eigenstates of $\hat{x}$ with eigenvalues respectively $-1,1$. We can also define the *not* operator with respect to the other axis of the [[Bloch sphere]]
$$
Y = \left[ \begin{matrix}
0  & -i \\
i  & 0
\end{matrix} \right]  \qquad Z = \left[ \begin{matrix}
1  & 0 \\
0  & -1
\end{matrix} \right] 
$$
### Phase shift quantum gate

The $\hat{R}_{\phi}$ gate, or phase shift gate with $\phi$ *shift* is defined as
$$
\hat{R}_{\phi}\ket{0}  = \ket{0}  \qquad \hat{R}_{\phi}\ket{1}  = e^{i\phi}\ket{1}  
$$
The matrix is
$$
R_{\phi} = \left[ \begin{matrix}
1   & 0 \\
0 & e^{i\phi}
\end{matrix} \right] 
$$
This means that the matrix is formed by its eigenstates with the eigenvalues on the diagonal. From this we can see some notable gates
- $\hat{Z}$-Pauli gate  $\hat{R}_{\pi} \equiv \hat{Z}$ which has $1,-1$ as eigenvalues
- $\hat{S}$-Pauli gate $\hat{R}_{\frac{\pi}{2}} \equiv \hat{S}$ which has $1,i$ as eigenvalues
- $\hat{T}$-Pauli gate $\hat{R}_{\frac{\pi}{4}} \equiv \hat{T}$ which has $1,e^{i\pi/4}$ as eigenvalues
### Hadamard gate

This gate is very important and used, it maps like this
$$
\ket{0}  \xrightarrow{\hat{H}} \ket{+} \qquad\ket{1} \xrightarrow{\hat{H}} \ket{ -}  
$$
This gate introduces the superposition on the states $\ket{0}$ and $\ket{1}$. It's matrix is
$$
H = \left[ \begin{matrix}
\frac{1}{\sqrt{ 2 }}  & \frac{1}{\sqrt{ 2 }} \\
\frac{1}{\sqrt{ 2 }}  & -\frac{1}{\sqrt{ 2 }}
\end{matrix} \right] = \frac{1}{\sqrt{ 2 }}\left[ \begin{matrix}
1  & 1 \\
1  & -1
\end{matrix} \right] 
$$


