---
tags:
  - parallel_computing
---
A thread is an independent stream of instructions withing a [[Process]] and they can be scheduled to run by the operating system. Threads have local resources and can access the shared process resources.

![[thread.png]]

Each thread can be sees as any procedure that runs independently from its main program. Upon creation they duplicate only the bare minimum resources needed for their execution, this means that they are lighter than a [[Process]].

All the threads inside a program exists within a process and share most of the resources. This means that there is **implicit communication** when accessing shared variables and that this access requires proper explicit [[Synchronization]].
### Threaded models
- Manager/worker
- Pipeline
