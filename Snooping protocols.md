---
tags:
  - computer_architecture
---
These protocols are used in [[Multi-processors]] architecture to deal with the problem of cache coherence by keeping track of the sharing status of each block with a cache controller that monitors the bus.
### Snoopy bus

All cache controllers monitor on the bus to determine whether or not they have a copy of the block. Every cache maintains a copy of the shared block along with it's sharing state. When accessing the block the processor has to make a request to all other processors in broadcast.
This is suitable for a **centralized shared memory architecture** and small scale multiprocessors.

The problem with this architecture is that it causes a lot of stalls since every bus transactions checks the cache address tags and make the cache unavailable. To reduce this interference we just duplicate the address tag portion of the cache.

>[!note]
>This architecture needs an extra read port to access the duplicate data
### Write invalidate protocol

The writing processors issues an **invalidation** signal over the bus to cause all copies in other caches to be invalidated before changing its local copy. **Only the first change** gets broadcasted on the bus. All caches must check if they have a copy of the data and invalidate it. This provides similar benefits to write back protocols in terms of reducing demands on bus bandwidth.
### Write update protocol

The writing processors broadcasts the new data over the bus, all caches must check if they have a copy of the data and, if so, **update it**. This scheme requires the continuous broadcast of writes to shared data, thus reducing latency at the cost of needing high bandwidth.
### MSI protocol

Each cache block can be in one of these $3$ states:
1) Modified of dirty $\to$ cache has only copy, its writable, and dirty -- it cannot be shared anymore
2) Shared or clean $\to$ the block can be read
3) Invalid $\to$ the data is not valid

Consequently each memory block can be in these $3$ states:
1) Shared $\to$ in all caches and clean
2) Modified $\to$ in one dirty cache
3) Uncached

![[cache fsm.png]]
#### MESI protocol

Each cache block can be in one of these $4$ states:
1) Modified of dirty $\to$ cache has only copy, its writable, and dirty -- it cannot be shared anymore
2) Exclusive $\to$ the block is clean and cache has the only copy
3) Shared or clean $\to$ the block can be read
4) Invalid $\to$ the data is not valid

>[!important]
>The advantage of the MESI protocol is that a write on an exclusive block does not require to send the invalidation signal on the bus since no other copies exists.

