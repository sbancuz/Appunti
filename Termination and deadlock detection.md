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
### Diffusing computation

In diffusing computations initially all processes are idle except the init one. A process is activated only by a message being sent to it and the termination is detected with the Dijkstra-Scholten method. 
#### Dijkstra-Scholten termination detection

Each node keeps track of nodes it sends a message to.  If a node was already awake when the message arrived, then it is already part of the tree, and should not be added as a child of the sender. When a node has no more children and it is idle, it tells its parent to remove it as a child.
### Distributed deadlock detection

The is no coordinator in charge of building the global wait-for graph. Processes are allowed to request multiple resources simultaneously and when a process does get blocked, it sends a probe message to the processes holding resources it wants to acquire. When a probe makes it back to the initiator it means that a cycle occurred. In this case the initiator may abort the connection or it may pick the process with the higher identifier and kills it.
### Obermarck algorithm

This is another algorithm to prevent deadlocks in a [[distributed system]] and it requires an algorithm that can detect cycles in [[Graphs]], to be more specific, in the wait for graph. It consists of 4 steps:
1) Get the graph info from the *previous* nodes
2) Update the local graph by merging the information
3) Check for cycles, if found select one process and kill it
4) Send away the updated graph to the *next* nodes