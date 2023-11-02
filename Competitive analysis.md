---
tags:
  - parallel_computing
---
In competitive analysis one algorithm must execute the operation immediately without any knowledge of the future and it's objective is to minimize the cost of the operations. This is known as an **on-line** algorithm and the opposite is known as **off-line**.

An on-line algorithm is $\alpha$-competitive if there exists a constant $k$ such that for any sequence $S$ of operations 
$$
C_{A}(S) \leq \alpha C_{opt}(S) + k
$$
where opt is the optimal off-line algorithm.

One example of algorithm that competitive analysis is used for is [[Self-organizing lists]]