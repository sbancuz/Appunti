---
tags:
  - parallel_computing
---
Shared memory is an efficient means of passing data between processes. In a shared memory model, parallel processes share a global address space that they read and write to asynchronously. This is dangerous because it might lead to race conditions.

![[shared mem.png]]

