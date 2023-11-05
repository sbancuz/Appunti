---
tags:
  - parallel_computing
---
To avoid the difficulties of automatically parallelizing a sequential program written in a sequential programming language, is to directly describing the problem in a parallel manner with high level abstractions that can easily express parallelizable assembly instructions.

There is not a single kind of parallelism but there could be identified 4 derived from the principle of instruction parallelism and data parallelism:
- SISD
- SIMD
- MISD
- MIMD

There are also level of parallelism:
- Bits
- Instruction
- Tasks

Tasks can be pipelined to ensure their parallelism, this means that we can identify inside a sequential algorithm a dependency graph of instructions/tasks to be executed in parallel and/or out of order. The communication of the memory that creates this dependency of instructions is given by two main models:
- Shared memory $\to$ All the processors share a global memory with the same address space and modification of said memory can be seen by all the other processors
- Message passing $\to$ Each task has its private memory and the tasks communicate by explicitly sending and receiving messages