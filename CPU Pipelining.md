---
tags:
  - computer_architecture
---
Pipelining is a technique to increase throughput when scheduling operations, MIPS makes use of this execution schedule by using 4 register between the various phases of execution. This means that the time to execute for all the instructions is 5 cycles, but overall the speedup for the program is 5x at most. This can be measured with [[Performance metrics]].

![[pipelining.png]]

One important detail is that to perform pipelining we need to add **pipeline registers** to hold the intermediate values of the computation.

![[MIPS arch.png]]

A **hazard** is created whenever there is a dependence between instructions, and these instruction are close enough to cause an overlap in the instruction execution in the CPU, resulting in delays to make sure that instructions are still executed in the right order. Hazards can be categorized as
- [[Structural hazards]]
- [[Data hazards]]
- [[Control hazards]]
#### Dependence

All these problems fall under the same underlying region, **dependence**. If two instructions are dependent to each other, they cannot be executed in parallel, just in order or partially overlapped. There are 3 types of dependencies:
- True data dependencies / flow dependence
	An instruction $j$ is dependent on a data produces by $i$

- Name dependencies 
	Two instructions use the same memory location, these are the same as [[Parallelization#Data dependency]] when talking in general about parallelization. To resolve this problem, an easy fix would be to change the location where the data would be saved, like for example in another register. This specific action is called [[Register renaming]].

- Control dependencies
	A control dependence determines the ordering of the instructions and it's preserved by both the program order and the fact that an hazard cannot be allowed to happen before a branch direction is not known
### Multi cycle pipeline

Up until now we have considered **single issue** processors, i.e. one instruction per clock cycle. This is not ideal since requesting some memory or even some instructions may take more than one cycle to resolve, this means that the write back instruction will be delayed.  

To solve this issue we need to execute instruction out of order while the other, more latent instructions, are executing. But this now creates problems with anti and output dependence.

![[multi pipe.png]]

The key idea to solve all these hazards is [[Dynamic scheduling]] and allow data independent instruction behind a stall to proceed -- all of this managed by the HW.

We can also define an exception to be **imprecise** when the processors state raises an exception, and the state produces is not the same as if the instruction where executed in-order. These type of exception are very hard to deal when they occur, because how would we know from what data to restart? So they have to be avoided like the plague.
### Multiple issue pipeline

Since we dealt with all types of hazards, how can we still increase performance? Well just issue multiple instructions per clock and extend the processor architecture to deal with it -- just put more ways to read registers and some other ALUs.

In this case the dynamic scheduler will have to work overtime to resolve all dependencies and maximize throughput.