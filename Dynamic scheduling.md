---
tags:
  - computer_architecture
---
We are trying to solve the problem of having hazards due to true data dependencies that cannot be solved by forwarding cause of **stalls** of the [[CPU Pipelining]]. The solution to this problem is to allow **data independent instructions** behind to proceed. 

>[!note]
>This generates out of order commits and execution
### Tomasulo dynamic scheduler

The idea is that this scheduler does is [[Register renaming]] to remove any WAW and WAR  hazards. This is achieved by using some buffers called **reservation stations** in front of the function units to hold pending operations before executing them. Tomasulo kind of works like [[CPU Pipelining#Scoreboard pipelining]], but the main difference is that we don't have a centralized buffer that will hold all pending operations, but a **distributed** one. The result of a computation is broadcasted to all the functional units and to all store buffers.

This scheduler is **in-order issue**, **out-of-order execution and completion**.

![[tomasulo.png]] 

There are 3 stages of the Tomasulo pipeline
1) Issue 
	Get an instruction from the instruction queue, check for structural hazards in the reserving stations (**RS**) in if needed add some stalls. If the operands are not yet ready in the register file (**RF**) then we need to keep track of the FU that will produce them. This is the step of [[Register renaming]].

2) Start execution
	Once both the operands and the functional units are ready we can start the execution. If the FU aren't yet ready, then just monitor the shared bus for the results that we need. 
	The loads and stores works a little bit differently, first they compute the effective address then they will try to execute. To preserve exception behavior no instruction can be executed until all branches before are resolved, if branch prediction is used, then the CPU must know the prediction correctness.

>[!Important]
> The load/store operation are kept in order

3) Write result
	Broadcast the result of the operations to the shared buffer and, if needed, write the result to the memory.
#### Drawbacks

The Tomasulo scheduling is very complex, in fact it takes a lot of hardware and power to run it. Also the performance is limited by the common data bus.

### [[Hardware based speculation#Speculative Dynamic scheduling Tomasulo dynamic scheduler]]
