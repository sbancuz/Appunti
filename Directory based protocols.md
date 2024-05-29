---
tags:
  - computer_architecture
---
This is a protocol used in [[Multi-processors]] architecture to maintain cache coherence. The sharing state of a block of physical memory is kept in just one location, a **directory**. Each entry in the directory is associated to each block in the main memory.

In a **centralized shared memory** there is a single directory associated to the main memory. For **shared memory architectures** the directory is distributed on the nodes to avoid bottlenecks. Even though the directory may be distributed, the sharing state of a block is only kept in one **single location**.

The physical address space is statically distributed to the nodes. To avoid broadcasts, we use a message passing protocol to access the directory. Just this fact makes this type of architecture more scalable.

The directory keeps state of:
- the coherence state of each block
- which processors have a copy of the block
- which processor is the owner

There are $3$ possible coherence states for each cache block in the directory
1) uncached $\to$ no processor has a copy of the cache block
2) shared $\to$ one or more processors have cache block and memory is up to date
3) modified $\to$ only one processor -- i.e. the owner -- has data that has been modified 

Each block in the cache can be in one of $3$ states:
1) modified (read/write) $\to$ the block is dirty and this processor is the only owner
2) shared (read only) $\to$ the block is valid and it's shared with other processors
3) invalid

The processors can be divided in $3$ types depending on their involvement
1) home node $\to$ where the memory resides
2) local node $\to$ where the request originates
3) remote node $\to$ where there is a shared copy

Directory based protocols must implement two primary operations: handling a **read miss** and a **shared write**.
On a **read miss**, the processor sends a miss requests from the local cache to the home directory to mark $P$ as read sharer. The directory will reply with the value from the home memory back to the local node.
On a **write miss**, the processor sends a miss request by the local cache to the home directory and to make $P$ the exclusive owner. The directory will reply with the value to the node, then the home will have to invalidate all other sharing remote caches.

![[directory fsm.png]]