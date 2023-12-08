---
tags:
  - parallel_computing
---
![[parallel tools.png]]

![[parallel tools 2.png]]

![[parallel vs overhead.png]]

![[parallel tools 3.png]]

### Pro vs Cons

#### VDHL

good: complete control on computation and memory with no overhead
bad: requires specific hardware and very difficult to learn.
#### [[MPI]]

good: can be adopted on different types of architectures and provides explicitly managed synchronization and data communication  
bad: lots of overhead and can be more difficult to use than shared memory
#### [[PThreads]]

good: full control over the application with explicit parallelism
bad: low level API with significant overhead, so it can be hard to scale
#### [[OpenMP]]

good: easy to learn and scalable. Also provides the option to execute sequentially
bad: mainly focused on shared memory homogeneous systems
#### CUDA

good: provides access to the GPU, and is quite easy to write with support of already optimized libraries
bad: NVIDIA only and difficult to extract massive parallelism from application
#### OpenCL

good: target independent and provides the same programming infrastructure for very heterogeneous architecture (CPU + GPU + FPGA)
bad: difficult programming paradigm and hides too much architecture details
#### Apache Spark

good: provides API for different languages that don't require parallelization and communication
bad: suitable only for big data and not yet utilized by the GPU