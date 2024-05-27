---
tags:
  - computer_architecture
---
The basic idea of this architecture is to load **sets** of data elements into **vector registers**, then we can perform operations on them. This means that a single instruction operates on vectors, it has a single program counter. The main benefit of this type of architecture is that it leverages memory bandwidth.  

![[vector ops.png]]

In vector processors each result is **independent** of previous results. And, since they are mostly used whenever there is a lot of work -- i.e. in loops -- they can just leverage the instruction cache and prefetch data. 

There are also a couple of classes of vector architectures
- Memory-memory
- Vector-register