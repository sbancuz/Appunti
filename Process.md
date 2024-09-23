---
tags:
  - parallel_computing
  - OS
---
A UNIX process is an execution created by the [[operating system]]. Each process contains information about program resources and program executions state. This is the **Process control block** or **PCB**
- PID
- Process context $\to$ Values of registers and program counters
- [[Virtual memory]] mappings 
- Open files $\to$ This includes memory mapped files
- Credentials (UID, GID) $\to$ They enforce security and privacy
- Signals handling info $\to$ They allow to manage asynchronous events like interrupts
- Controlling terminal $\to$ These allow to manage resource allocations
- Priority and accounting statistics $\to$ They manager process execution order

Each process can be in a **state** depending on its actual conditions, they dictate what a process can or can't do and what resource it's using.

![[Tasks state machine.png]]

If a process terminates, it can become a **zombie**. This state means that it has completed and it's just waiting for the parent process to remove it.
