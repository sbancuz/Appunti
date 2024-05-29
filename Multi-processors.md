---
tags:
  - computer_architecture
---
Multi-processors now play a major role form embedded to high end general-purpose computing. It's main goal is very high-end performance, scalability and reliability. This type of architecture refers to tightly coupled processors whose coordination and usage is controlled by a single operating system that usually share memory through a shared address space.

>[!note]
>There is also **multi cores** that is when all cores are in the same chip
### Design issues

There are some decisions to take when designing a multi-processor
- How many processors?
- How powerful are processors?
- How do we connect all the processors?
	There are 2 ways:
	1) Single bus 
		This imposes a constraint on the number of processors connected -- $36$ for now. The connection medium is between the processors and memory. The bus is used for every access.
		
	2) Interconnection network 
		This is just more busses, more consistent performance per unit cost. Memory is attached to each processor and the busses are used only of IPC. There are a lot of topologies to create the network:
		- Ring $\to$ capable of many simultaneous transfers, the communication may pass by intermediates
		- Mesh $\to$ this can be either a $2D$ mesh, a cube or even an hypercube
		- N-cube
		- Crossbar $\to$ every processor has a bidirectional dedicated communication link to everything

- How do parallel processors share data?
	There are two main ideas:
	1) Single logically shared address space 
		A memory reference can be made by any processor to any memory location. This is a [[Shared memory model]]. Processors communicate using shared variables in memory. This imposes a **cache coherence problem** among processors.
	
	2) Multiple private address spaces
		The processors communicate among them through send and receives. This is a [[Distributed memory model]] using message passing. Processors communicate among them through sending/receiving messages. All accesses to private memory of other processors is explicit. No **cache coherence problem**.

- Where to place the physical memory?
	The memory can be either centralized or not. In the first case the access time is **uniform** no matter the location, hence **Uniform Memory Access**. The latter since the memory is divided the access time is no longer uniform and the time to access memory depends on the location, hence **Non Uniform Memory Access**. 

>[!important]
>Physical memory location and address spaces are two very different problems even though it may seem the same. 

- How do parallel processors cooperate and coordinate?
- How to program processors?
	There are a couple of paradigms:
	1) Multi programming $\to$ no communication, a lot of jobs
	2) Shared address space $\to$ communication via loads and stores
	3) Message passing $\to$ communication via sends and receive
	4) Data parallelism $\to$ [[SIMD]]

- How to maintain cache coherence?
	A program running on multiple processors will normally have **multiple copies** of the same data in several caches. In a coherent multiprocessor the caches should provide both **migration** and **replication** of shared data items. To maintain coherence we need some **cache coherent protocols**, there are 2 classes:
	1) Snooping protocols
		Each core keeps track of the sharing status of each block with a cache controller that monitors the bus
	
	2) Directory based protocols
		The sharing status of each block is kept in one location, called a **directory**.
	
	These protocols ensure that all writes by one processor are eventually visible to other processors, for one memory address.
	

- How to maintain memory consistency?
	This is **complementary** to memory coherence. This defines the behavior of reads and writes with respect to accesses to other memory locations. A memory consistency model gives the rules on when a write by one processor can be observed by a read on another. Just like the others we can achieve this either through **shared memory** or **message passing**.

- How to evaluate system performance?