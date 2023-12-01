---
tags: [gal]
---
This value geometrically represent the factor for which the vector space is stretched when multiplying the matrix.
To compute it we use [[Sarrus triangle]] for $3x3$ or the Laplace method for the other ones.
$$
\det A = \sum_{j=1}^{n}a_{ij}A_{ij}
$$
where $A_{ij}$ is the [[Algebraic complement]].
### Properties

- Normalization => $\det I=1$
- Symmetry => $\det A=\det A^{t}$
- Binet's formula => $\det AB=\det A\det B$
- $\det A^{-1}=\frac{1}{\det A}$
- Alternation => iff I exchange 2 rows $\det A=-\det A'$
- Multilinearity => iff multiply a row by a scalar  $\det A=t\det A'$
- If a row is the sum of $2$ rows => $\det A=\det A'+\det A''$
- If $2$ rows are not linearly independent => $\det A=0$
