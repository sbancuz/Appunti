---
tags:
  - parallel_computing
---
### Keygen

1) Randomly select 2 primes $p$ and $q$ of similar size, each with $l+1$ bits $(l\geq 500)$
2) Let $n =pq$
3) Let $e$ be an integer that does not divide $(p-1)(q-1)$ i.e. relatively prime
4) Calculate $d = e^{-1} \text{ mod } (p-1)(q-1)$
5) $P = (e,n)$
6) $S = (d,n)$

This works because finding the greatest common divisor is a computationally complex problem.