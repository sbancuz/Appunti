---
tags:
  - computer_architecture
---
The main goal of this type of scheduling is to **statically reorder** instructions in object code so that they are executed in a minimum amount of time and keep the semantically correct order.

The idea is to decompose the code in **basic blocks** that each have a single entry point and a single exit point. So they can be represented with a **dependence graph**

![[VLIW dep graph.png]]

The scheduling problem consists of assigning the cycle of execution to each operation in the graph. 

The simplest type of scheduling occurs when we just want to minimize the time without caring about the resources available and required. To implement this we just need a **ready list** and an **ASAP algorithm** -- assign each node in the ready list as soon as possible.

Now if we introduce the **resource constraint** things get a little bit more complicated. To bootstrap this process we put the operation on top of the graph in the ready set. For each cycle try to schedule operations from the ready set that can fill the available resource slots. Always choose the **highest priority** node when possible.

