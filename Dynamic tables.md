---
tags:
  - parallel_computing
---
The idea is whenever the table overflows, we grow the table size by allocating a new larger table and moving all the items to the new table. Basically using **realloc** to create the standard dynamic array structure with items, capacity and count.

The worst case for time [[Complexity of an algorithm]] for inserting $n$ items is $\Theta(n^{2})$ because the worst case for an insertion is $\Theta(n)$ and that happens when we have move every time the isn't enough space. But in reality, at least not when the vector is small and we never allocate more than one new item at a time, this case happens very rarely and thus the wort case is $\Theta(n)$ and the average case is $\Theta(1)$.

