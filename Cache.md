---
tags:
  - computer_architecture
---
A cache is a type of **volatile** memory that is used to improve the performance of a process. There can be two types of caches:
- A logical cache $\to$ a data structure used in a program to speed up the computation
- A physical cache $\to$ a chip that gives the illusion of a very fast and large memory
### Physical caches

Caches are designed in a memory hierarchy ($L1, L 2, L 3$) and are designed based on two main principles:
- **temporal locality** $\to$ the data put in cache is likely to be reused in the near future
- **spatial locality** $\to$ when there is a reference to a memory, is likely that the program will need the data that is *near*

>[!tip]
>Highest level cache is the $L 1$ cache

The minimum chunk of data that can be copied to cache is called **cache line**, to exploit spatial locality the cache line size must be a multiple of a word in the register size. When we find some data in the cache it's called a **cache hit**, if not it will be a **cache miss**.

>[!warning]
>A cache miss is very slow! From going from one level to the next is one order of magnitude slower! See also [[Performance metrics]]
#### Cache structure

All cache lines are divide in 3 parts:
- validity bit $\to$ if the position contains valid data or not, at boot they are all invalid
- cache tags $\to$ contains the value that univocally identifies the memory address corresponding to the stored data
- cache data $\to$ the actual data of the cache line

![[cache.png]]
#### Cache insertion

How do we put data in the cache? We 3 methods depending on the cache architecture
- Direct mapping
	Each memory location maps only to one cache location
$$
(\text{Block address})_{\text{cache}} =  (\text{Block address})_{\text{memory}}  +  \text{mod}(\#\text{cache lines})
$$
- Fully associative cache
	The memory block can be put in any position of the cache, the problem is that we have to search the data in all cache lines

- n-way Set-associative cache
	This is a middle ground of the 2 architectures, the memory blocks can be put in any cache line of the set
$$
(\text{Set})_{\text{cache}} =  (\text{Block address})_{\text{memory}}  +  \text{mod}(\#\text{sets})
$$
To actually choose the block when reading we can just use an **LRU policy**, and on a write we can use a **write-back** policy and write it back to lower memory only when the cache line is replaced because of a miss. Upon a miss when writing we can use a **write allocate** that allocates a new cache line.

![[cache summary.png]]