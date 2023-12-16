---
tags:
  - parallel_computing
---
### Gather

This is a composition of a map and random serial reads. This yields a collection who's elements are of the same type of the input but follow the structure given by the indices collection.

![[gather.png]]
#### Shift

This is a special case of a gather that moves data to the left or right in memory and data accesses are offset by fixed distances.

![[shift.png]]
#### Zip/unzip

The zip defines the operation of combining two arrays into one and the unzip can be seen as the inverse.

![[zip.png]]

### Scatter

The scatter is the inverse of the gather, the indices indicate where each input element should write.

![[Scatter.png]]

In parallel computation, multiple writes into the same memory space is considered as a race condition. This is a problem because it makes the output non deterministic.

To fix this we can create rules to define how should we handle these conflicts:
- Atomic scatter -> operations are performed atomically, this is still non-deterministic but the data is complete
- Permutation scatter -> collisions are illegal by definition
- Merge scatter -> associative and commutative operators are provided to handle conflicts
- Priority scatter -> each element has a priority depending on its position and dictates what gets written
