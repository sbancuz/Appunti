---
tags:
  - parallel_computing
---
The pack patter is a parallel pattern used to reduce space of a collection by removed the unused allocations. With this operation the elements marked **false** are discarded and are put in a new structure with the same order as the original one. There also exists an inverse operation called **unpack**

![[pack.png]]

This pattern is not easy to implement in a parallel way because it's hard to know where to put an element since we don't know how many elements were accepted before.
#### Split

It's a generalization of the pack pattern in which elements are moved to upper or lower half of output collection based on some state, it does not lose information.

![[split.png]]
#### Unsplit

Inverse of the split.

![[unsplit.png]]
#### Bin

It generalizes the split even more to have more categories.

![[bin.png]]
#### Expand

Each element can output any number of elements

![[expand.png]]
### Unpack

There is also the inverse unpack operator that given the same data on which elements were kept and which were discarded, it spreads them back in their original locations.