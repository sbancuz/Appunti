---
tags:
  - computer_architecture
---
The main difference from software [[Threads]] is that there is no need for a context switch by the operating system. In fact all the multiple threads are managed only by the hardware, hence the name. 

>[!note]
>This is the **hyperthreading** in intel processors

The main idea with hardware threads is that when we need to perform a stall on some thread, we can just begin to execute some other instruction flow.

>[!important]
>The **state** of the register file needs to be preserved between switches. This means that we need multiple register files and program counters. One for each hardware thread. The operational units can be **shared**.

There are $3$ types of hardware multi-threading:
- Coarse grained multithreading 
	when a thread is stalled, another one can be executed. This will hide cache misses behind some other execution. The problem is that when switching we need to empty the pipeline, so it takes a couple of cycles to make a context switch so it only reduces the cost of **high cost stalls**.

- Fine grained multithreading 
	switch threads on each instruction in a round robin way. This can hide all stalls but it slows down the execution of individual threads

- Simultaneously multithreading
	multiple threads are using the multiple issue slots in a single clock cycle. The idea for this mode is that a CPU has more functional units than a thread can use. 

![[multithreading.png]]

