---
tags:
  - distributed_systems
aliases:
  - termination detection
  - deadlock detection
---
In a distributed system we often want to know when a computation has completed or deadlocked. This means that all processes are idle and no messages are present in the system. I this case [[Logging]] is used, but it requires that the channels must be empty.
### Simple solution

A lets call a process $Q$ predecessor of the process $P$ from which it already received the first marker. The successors of $P$ are all those processes $P$ sent the marker. When a process finishes its part of the snapshot, it sends a DONE message back to its predecessors only if its successors have returned a DONE message and $P$ has not received any message between the point it recorded its state and the point it had received the first marker. In any other case $p$ sends a CONTINUE. When the initiator receives all DONE the computation is over.