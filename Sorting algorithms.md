---
tags:
  - parallel_computing
  - coding
---
### Comparison sorts 

Comparison based algorithms are such that they only use comparison in order to sort an array.
Some examples are:
- [[Merge sort]]
- [[Quicksort]]
- [[Insertion sort]]

The best worst-case running time that we've seen is $O(n \log n)$. This can be proven as such, a tree must contain $\geq n!$. 
A height $h$ binary-decision tree has $\leq 2^{h}$ leaves, thus $n!\leq 2^{n}$
$$
h\geq \log(n!) \geq \log\left( \left( \frac{n}{e} \right)^{n} \right) = n \log n - n \log e
$$
### Other sorts

- [[Counting sort]]
- [[Radix sort]]
### Properties
- [[Stable sorting algorithm]]
- Adaptive
- In-place
- Online