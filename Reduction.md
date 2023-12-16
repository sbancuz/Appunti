---
tags:
  - parallel_computing
---
Reduce is used to combine a collection of elements into one summary value using an **associative** combiner function.

![[reduction.png]]

>[!tip]
>For big parallelizable workloads you can tile reductions together.
### Scan

The scan pattern is a generalization of the Reduction because it also produces partial results and can be divided in:
- Inclusive scan -> current element is used in the partial
- Exclusive scan -> current element is not in the partial reduction