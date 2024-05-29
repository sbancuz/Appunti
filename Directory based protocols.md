---
tags:
  - computer_architecture
---
This is a protocol used in [[Multi-processors]] architecture to maintain cache coherence. The sharing state of a block of physical memory is kept in just one location, a **directory**. Each entry in the directory is associated to each block in the main memory.

In a **centralized shared memory** there is a single directory associated to the main memory. For **shared memory architectures** the directory is distributed on the nodes to avoid bottlenecks. Even though the directory may be distributed, the sharing state of a block is only kept in one **single location**.

The physical address space is statically distributed to the nodes.