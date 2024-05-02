---
tags:
  - quantum
---
We can define the projective quantum [[measurement]] of an observable $A$ as **random** and **discontinuous irreversible** process. This is because measuring an observable perturbs the system, thus augmenting entropy. We describe this process as an orthogonal projection -- at random according to some rule for calculating the probabilities -- on to an eigenfunction of the hermitian operator $\hat{A}$. This process of measurement is also called the **collapse of the wave function**.

>[!important]
>The measurement will put the eigenfunction $\phi$ into a well-defined state.

Now for simplicity we consider a non-degenerate discrete spectrum observable $A$
$$
\text{Discrete set of orthonormal eigenfunctions } : \{ \phi_{i}| i=1,\dots,D-1 \}
$$
The fact that this set is orthonormal means that it's also a basis for the Hilbert space, so it implies
$$
\left< \phi_{n}|\phi_{m} \right>  = \delta_{nm}
$$
From this we can define the **eigenspace for the eigenvalue $a$** as the subset of $\mathcal H$ with dimension $1\leq g \leq D$ where
$$
\hat{A}\phi' = a\phi'
$$
$g$ is called the **multiplicity or order of degeneracy** of the eigenvalue $a$.

>[!note]
>An eigenvalue is said to be non degenerate if it's multiplicity is $1$. Moreover an eigenfunction when all it's eigenvalues are non degenerate.
>
>
### Born's rule
Now, given a non-measured quantum state $\psi$ and an orthogonal projector $\hat{\Pi}$ onto the eigenfunction $\phi_{n}$ selected with some probability $P_{n}$ we can formally define the measurement as
$$
c_{n}\phi_{n} = \hat{\Pi}_{i\phi_{m}}\psi
$$
This probability of **measuring** $a_{n}$ from the observable $A$ can be calculated
$$
P_{n} = \frac{||\hat{\Pi}_{\phi_{n}}\psi||^{2}}{||\psi||^{2}} = \frac{||c_{n}\phi_{n}||^{2}}{||\psi||^{2}} = |c_{n}|^{2} \frac{||\phi_{n}||^{2}}{||\psi||^{2}} = \frac{|\left< \phi_{n} | \psi \right> |^{2}}{||\phi_{n}||^{2}||\psi||^{2}}
$$
And when we consider a normalized wave function we get
$$
P_{n} = |c_{n}|^{2} \qquad c = \sqrt{ P_{n} }e^{i\gamma} \qquad |c| = \sqrt{ P_{n} }
$$
>[!important]
>This corresponds to the wave collapse onto the eigenstate $c\phi_{n}$
