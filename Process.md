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

 [[CPU multiplexing#Task]] can be in four different states
- TASK_RUNNING
	This represents a task that is either running or waiting to run, but present in a run queue
	
- TASK_INTERRUPTIBLE 
	The task is sleeping and is waiting for a single to wake up. This usually means that the process is waiting on some shared resource
	
- TASK_UNINTERRUPTIBLE
	This task is sleeping and it won't wake up even if it receives a signal. This is less commonly used and is applicable when the event is expected to occur promptly. Note that tasks in this state are not killable.
	
- TASK_DEAD
	This is a temporary state where a task is finished and no longer executing but its still allocated in memory and waiting for the parent process to collect its exit code and resources. Dead processes are also called **zombies**.