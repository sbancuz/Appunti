---
tags:
  - parallel_computing
---
### Gather

This is a composition of a map and random serial reads. This yields a collection who's elements are of the same type of the input but follow the structure given by the indices collection.

![[gather.png]]
### Scatter

The scatter is the inverse of the gather, the indices indicate where each input element should write.

![[Scatter.png]]