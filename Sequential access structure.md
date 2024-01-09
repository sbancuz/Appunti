---
tags:
  - databases
---
The memory here is arranged like a [[Linked list]], so the blocks are arranged in a sequential order. In the actual memory blocks can either be stored in contiguous way or sparse. 

They can be arranged in 2 ways:
- **entry sequenced** $\to$ sequence of tuples dictated by their order of entry
- **sequentially ordered** $\to$ tuples are ordered according to the value of a key
### Entry sequenced

These types of structure are optimal for insertions and sequential reading -- no conditions. To use them with conditions we can use them in conjunction with indexes.
### Sequentially ordered

Tuple are sorted by their keys and as such, it's very efficient to query ranges or define ordering. The problem presents itself when inserting or update of a tuple. These are a bit more heavy since the table needs to be reorganized.

![[seq acc struc.png]]