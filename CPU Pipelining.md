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

There can be $2$ types of multi-cycle pipeline
- In order issue && In order commit $\to$ avoids WAR and WAW hazards and with a precise exception model
- In order issue && out of order commit $\to$ split ID and Issue in 2 stages, we have WAR and WAW

To solve this issue we need to execute instruction out of order while the other, more latent instructions, are executing. But this now creates problems with anti and output dependence.

![[multi pipe.png]]

The key idea to solve all these hazards is [[Dynamic scheduling]] and allow data independent instruction behind a stall to proceed -- all of this managed by the HW.

We can also define an exception to be **imprecise** when the processors state raises an exception, and the state produces is not the same as if the instruction where executed in-order. These type of exception are very hard to deal when they occur, because how would we know from what data to restart? So they have to be avoided like the plague.
### Multiple issue pipeline

Since we dealt with all types of hazards, how can we still increase performance? Well just issue multiple instructions per clock and extend the processor architecture to deal with it -- just put more ways to read registers and some other ALUs.

Multiple issues allow for an ideal **instruction per clock** to be 
$$
IPC_{ideal} > 1 \qquad CPI_{ideal} < 1
$$
In this case the dynamic scheduler will have to work overtime to resolve all dependencies and maximize throughput.
#### Very long instruction word

This is another type of architecture in contrast with [[dynamic scheduling]]. This takes advantage of static scheduling to deal with all the dependencies of the code to help scale performance better, in fact a pure dynamic scheduled approach has an upper bound of issues of 4. 
### Scoreboard pipelining

This is a **centralized*** solution to deal with both hazard detection and resolution. Every instruction goes through a **scoreboard** table that is used to determine when the instruction can read its operands and begin the execution.

The main idea is to keep track of the status of instructions, functional units and registers with this table. The scoreboard is structured to keep track of 
- Instruction status
- Functional unit status $\to$ more precisely with: busy, Op, Destination, Source, Functional units and Ready flags
- Register result status

We start by considering a **single-issue** processors where the IF are executed in-order, but the execution overall can be out-of-order -- this means that we also can have anti and output dependencies. Execution and memory stages can also take multiple cycles to finish.

>[!warning]
>We can't have forwarding and we can deal with imprecise interrupts

Scoreboard allows **data independent instructions behind a stall to proceed**. We can distinguish when an instruction begins execution and when it completes. 

![[scoreboard.png]]

The ID stage of an instruction can be divided in two stages:
- Issue $\to$ the decoding part that can check for structural hazards
- Read operands $\to$ Wait until all data hazards are resolved

>[!note]
>Since this is out-of-order commit, WAR and WAW can still occur

To deal with anti-dependency we can read registers only during the Read Operands stage. To deal with Output dependency we can stall the new instruction until the previous one finishes.

![[scoreboard arch.png]]
### Tomasulo dynamic scheduler

The idea is that this scheduler does is [[Register renaming]] to remove any WAW and WAR  hazards. This is achieved by using some buffers called **reservation stations** in front of the function units to hold pending operations before executing them. Tomasulo kind of works like a scoreboard, but the main difference is that we don't have a centralized buffer that will hold all pending operations, but a distributed one. The result of a computation is broadcasted to all the functional units and to all store buffers.

![[tomasulo.png]] 

There are 3 stages of the Tomasulo pipeline
1) Issue 
	Get an instruction from the instruction queue, check for structural hazards in the reserving stations (**RS**) in if needed add some stalls. If the operands are not yet ready in the register file (**RF**) then we need to keep track of the FU that will produce them. This is the step of renaming.

2) Start execution
	Once both the operands and the functional units are ready we can start the execution, if they aren't, just monitor the shared bus for the results that we need. The loads and stores works a little bit differently, first they compute the effective address then they will try to execute. To preserve exception behavior no instruction can be executed until all branches before are resolved, if branch prediction is used, then the CPU must know the prediction correctness.

>[!Important]
> The load/store operation are kept in order

3) Write result
	Broadcast the result of the operations to the shared buffer and, if needed, write the result to the memory.