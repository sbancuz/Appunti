---
tags:
  - parallel_computing
aliases:
  - map
---
A map is a high order function that takes in input a pure function $f$ and a collection of data and applies $f$ to each element of the collection. Its output will be a collection containing the results preserving the order. A map is a good fit if the tasks are independent and balanced in term of work to do. The map operation is useful in [[Divide and conquer approach]].

![[map.png]]

This operation is embarrassingly parallel: $T(\infty) = O(1)$ plus a $O(\log n)$ of overhead to divide the work.

The map operation can also be generalized to take as input multiple collections and operate on all of them at the same time and is called **n-ary** map. 

### Optimization: Sequence of maps

Often we use several map one after the other, and the naive implementation would consist in storing in cache all the intermediate results of the operation, thus overwhelming it. To resolve this problem we can fuse together all the operation in one single map.

![[compress map.png]]

>[!note]
>Ideally we want to be able to perform the operation using only CPU registers.
### Optimization: Cache fusion

Sometimes it is impractical to to fuse together operations, instead we can break the work into blocks and dividing these blocks between all the CPUs.

![[cache fusion.png]]


