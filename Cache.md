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
(\text{Block address})_{\text{cache}} =  (\text{Block address})_{\text{memory}}  \text{mod}(\#\text{cache lines})
$$
- Fully associative cache
	The memory block can be put in any position of the cache, the problem is that we have to search the data in all cache lines

- n-way Set-associative cache
	This is a middle ground of the 2 architectures, the memory blocks can be put in any cache line of the set
$$
\begin{align}
(\text{Set})_{\text{cache}}  & =  (\text{Block address})_{\text{memory}}  \text{mod}(\#\text{sets}) \\ \\
\# \text{Blocks} = \frac{\text{Cache size}}{\text{Block size}}  &\qquad \# \text{Sets} = \frac{\text{Cache size}}{\text{Block size} \times n} 
\end{align}
$$
To actually choose the block when reading we can just use an **LRU policy**, and on a write we can use a **write-back** policy and write it back to lower memory only when the cache line is replaced because of a miss. Upon a miss when writing we can use a **write allocate** that allocates a new cache line.
### What happens on a write?

In the case that we have a hit we have to make a choice:
- Write-through 
	The information is written to both the block in the cache and to the block in lower level memory. To be effective we need to add a **write FIFO buffer** to avoid write stall when writing to lower memory.  This has the the advantage of keeping the memory always up to date.

- Write-back
	The information is written only to the block in the cache and it gets written in memory **only** when it's replaced due to a miss. To implement this we need a **dirty bit** in each cache block. This has the advantage of few writes in the main memory in the case of multiple writes on the same cache block.


![[cache summary.png]]

### Cache misses

There are $4$ major categories of cache misses:
- Compulsory misses
	The first access to a block will obviously not be in a cache, so the block must be loaded from the main memory. This is also called a **cold start miss**.

- Capacity misses
	If the cache cannot contain all the blocks needed during execution of a program, capacity misses occur when a block is being replaced and later retrieved for reuse.

- Conflict misses
	If the block placement strategy is set associative or direct mapped, conflict misses will occur because a block is replaced and later retrieved and other blocks map to the **same location**.

- Coherence misses
	Caused by cache coherence in multiprocessor architecture. Not explained further.
### Improve cache performance

The overall goal when optimizing performance of a cache is to balance fast hits and few misses by impacting $3$ metrics:
- Reduce miss rate
	1) The obvious way to resolve this problem is just to have a large cache size at the cost of hit time, area, power consumption and cost. 
	
	1) Another idea is to have a larger block size. This will reduce compulsory misses by taking advantage of spatial locality, at the cost of an increased miss penalty and a higher number of conflict misses.
	
	2) When using set-associative caches, to augment the associativity at the cost of hit time, area, power and cost.
$$
\text{Miss cache rate size } N \approx \text{Miss rate 2-way cache size } N/2
$$
- 
	3) To further increase associativity we can use **multi-banked caches**. So instead of treating the cache as a single block of memory, we use the cache as a collection of **independent banks** to support simultaneous access. To also support simultaneous access we spread the address space across banks.
	
	4) Use **victim caches**, a small fully associative cache used as a buffer to place data discarded from cache to better exploit temporal locality. They are put in between the levels of caches. If the block is found in this cache the victim block and the cache blocks will be swapped.
	
	5) Use pseudo associativity and way prediction. Basically divide the cache in two banks in a sort of associativity. If the prediction is correct then good, fast hist times, retrieve. If we have a misprediction, check the second bank, we call this a slow hit. Otherwise go to the next level.
	
	6) Exploit data locality and prefetch next instructions or data before they are requested by the processor. This can be done either in cache or in an **external stream buffer** . This relies on some extra memory bandwidth that can be used without paying some penalty.
	
	7) Software prefetching, the compiler can also help when prefetching data by leading the registers and the cache.
	
	8) Apply some code optimization by profiling the applications to improve data locality. This can be done by merging arrays, loop interchanging, loop fusing and loop blocking. 

- Reduce the miss penalty
	1) We prioritize the reads over the writes on miss. When using **write through**, if there are no conflicts, let the memory access continue sending the read miss before the write, otherwise the read miss has to wait until the write buffer is empty, but this might increase the read miss penalty. When using **write backs** we could copy the dirty block to a write buffer, then do the read miss, and finally do the write to the memory. This reduce CPU stalls since it restarts the execution as soon as do the read.
	
	2) Move sub blocks instead of full blocks. This needs some validity bits. The main drawback is that you can't exploit spatial locality quite as well.
	
	3) Usually the CPU needs just one word of the block on a miss, so just restart the execution after receiving it and asynchronously read the rest. This can be done in two ways: either we read normally until we get the desired word and restart, or read the critical word first, then the rest.
	
	4) Non blocking caches allows data to continue to supply cache hits during a previous miss.
	
	5) Add more levels of cache
	
	6) Merging write buffers, this allows the cache to hold different memory addresses withing each cache line
	
- Reduce the hit time
	1) Reduce the size of the cache, so it can operate with a fast clock rate using direct mapping. 
	
	2) Avoid address translation 
	
	3) Buffer the writes, and apply them all at once 

![[summary cache perf.png]]