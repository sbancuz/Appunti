---
tags:
  - OS
---
CPU multiplexing is a technique used to maximize resource utilization. This works by **context switching** to another process while the current one is idling, e.g. waiting for a keystroke. This allows other programs to execute concurrently. Of course just waiting till a process is idle isn't a great idea, it could easily happen that a process will hog all resources and never go to sleep, and other processes won't ever progress, so we introduce **time quantums**. 

![[time quantums.png]]

By multiplexing the CPU we can reduce latency significantly. Instead of waiting for a process to finish the kernel will allocate fixed time quantums and execute them in order. When a slice finished, the kernel will interrupt the [[process]] and resume with the next one. 

The kernel uses the [[Process]] control blocks to correctly perform **context switching**, i.e. pause the execution of a [[process]] and resume another one. This is achieved by saving and loading a [[process]] context onto the CPU registers.

![[context switch.png]]
### Scheduling policies

The decision of **what** to schedule is given solely to the kernel and by which scheduling policy it follows. In deciding what to run next, it should balance
- Fairness $\to$ don't starve processes
- Throughput $\to$ overall good performance
- Efficiency $\to$ minimize overheads of scheduling
- Priority $\to$ reflect relative importance of processes
- Deadlines $\to$ respect time boundaries

Of course there is no optimal policy for every occasion, some of these goals are in conflict: deadlines vs fairness. The solution of what to use will depend on the requirements of the OS, i.e. [[General purpose OS]] or [[RTOS]].

![[Scheduling techniques.png]]

