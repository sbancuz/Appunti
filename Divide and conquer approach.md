---
tags:
  - parallel_computing
---
The divide and conquer design paradigm is:
1) Divide the problem into sub-problems
2) Conquer the sub-problems by solving them recursively
3) Combine the results

### [[Merge sort]]

1) Divide: Trivial
2) Conquer: Recursively sort $2$ sub-arrays
3) Combine: Linear-time merge

### Binary search

1) Divide: check the middle element
2) Conquer: Recursively search $1$ sub-array
3) Combine: Trivial
$$
T(n) = T\left( \frac{n}{2} \right) + \Theta(1) = \Theta(\log(n))
$$

### Powering a number

The naive algorithm is $\Theta(n)$ where $n \in \mathbb N$
If we divide and conquer we can define this problem as
$$
a^{n} = \begin{cases}
a^{\frac{n}{2}}a^{\frac{n}{2}}  & \text{n is even} \\
a^{\frac{n - 1}{2}}a^{\frac{n - 1}{2}}a  & \text{n is odd}
\end{cases}
$$
So $T(n) = \Theta(\log n)$

### Matrix multiplication

The naive algorithm is $\Theta(n^{3})$ where $n \in \mathbb N$
Strassen algorithm