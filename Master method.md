---
tags:
  - parallel_computing
---
The master method applies to recurrences of the form
$$
T(n) = aT\left( \frac{n}{b} \right) + f(n)
$$
where $a>1,b>1$ and $f$ is asymptotically positive.

### Common cases

Compare $f(n)$ with $n^{\log_{b}a}$:
- $f(n)=O(n^{\log_{b}a-\epsilon})$ for some constant $\epsilon>0$ then $T(n) = \Theta(n^{\log_{b}a})$
- $f(n)=\theta(n^{\log_{b}a}\log^{k}n)$ for some constant $k>0$ then $T(n) = \Theta(n^{\log_{b}a}\log^{k+1}n)$
- $f(n)=\Omega(n^{\log_{b}a+\epsilon})$ for some constant $\epsilon>0$ then $T(n) = \Theta(f(n))$