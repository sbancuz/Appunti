---
tags: [gal]
alias: Matrice
---

Matrices are defined as $[N\times M]$ in which $N$ are the rows and  $M$ are the columns. A special case of matrices are [[Vectors]]

![[Identity matrix]]
### Properties

- Associativity  => $(v+w)+u=v+(w+u)$
- $V - V = \overline{0}$
- Distributive
- Mixed associativity => $(ts)v=t(sv)$
- Unity => 1$V=V$

>[!note]
>These properties are valid even for [[Vectors]]
### Operations

- Sum and scalar product
- Row-column product => $c_{ij}=\sum_{k=1}^{n}a_{ik}b_{kj}$ iff $[A,N]\times[N,B]$
- Transpose
- Power
- [[Inverse matrix]]
- [[Determinant]]
### Block matrices

$$
A=\left[
\begin{align}
A_{1} &  & 0 \\
0  & & A_{2}
\end{align}
\right]
$$

Where$A_{1}$ e $A_{2}$ are square matrices. These type of matrices also have the following properties
- $\det A= \det A_{1}\det A_{2}$
- The inverse is the composition of the inverse of all the submatrices
### Triangular matrices

These are matrices with all zeros above or under the main diagonal.
### Unimodular matrix

A matrix with integer components $m\times n$, $A$, is **unimodular** if for each non-singular submatrix $D$ being of maximum rank we get 
$$
\det(D) = \pm  1
$$
If we have that each of its non-singular square matrices is unimodular then it's called **totally unimodular**

A matrix $A$ with elements $0,\pm 1$ is TU if the following holds
- each column contains at most two non-null elements
- the indexes $\{ 1,\dots,m \}$ of the rows of $A$ can be partitioned into $I_{1},I_{2}$ such that
	- if a column has two elements with the same sign, the indexes of the rows do not belong to the same set
	- if a column has two elements with opposite signs, the indexes of the rows belong to the same set