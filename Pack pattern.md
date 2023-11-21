---
tags:
  - parallel_computing
---
The pack patter is a parallel pattern used to reduce space of a collection by removed the unused allocations. With this operation the elements marked **false** are discarded and are put in a new structure with the same order as the original one. There also exists an inverse operation called **unpack**

![[pack.png]]

This pattern is not easy to implement in a parallel way because it's hard to know where to put an element since we don't know how many elements were accepted before.