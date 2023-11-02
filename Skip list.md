---
tags:
  - parallel_computing
---
This is a randomized dynamic search structure that maintains a dynamic set of $n$ elements in $O(\log n )$ time [[Complexity of an algorithm]] per operation in expectation and with high probability.

This is implemented with a sorted linked list. Search is $\log n$ in the worst case.
Now suppose we have 2 sorted linked list and is a subset of the first one.

![[skiplist.png]]

The search cost is roughly 
$$
|L_{1}| + \frac{|L_{2}|}{|L_{1}|} = 2\sqrt{ n }
$$
This can become like a binary search structure by using $n$ linked list, and since it's just binary search the search cost is $\log n$. 

>[!warning] Invariant
>The bottom list contains all the elements

The ideal skip list maintains this binary search structure exactly, but this is not very feasible in practice so we aim to an approximation that works roughly in the same way. 

For the insertion we 
1) Search to see where $x$ would fit
2) Insert into the bottom list

To see if we have to add the $x$ to the next level is done by just flipping a coin so with $P=\frac{1}{2}$
The deletion is done by removing the item in all the list that contain it. 