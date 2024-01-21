---
tags:
  - databases
---
These are a set of techniques, typically used in databases, that are used to prevent the creation of deadlocks. There are two main techniques that are used:
- resource based prevention $\to$ restrict the lock on request
- transaction based prevention $\to$ restrictions based on the transaction id

Conflicts occur between a **requesting transaction** (RT) and a **conflicting transaction** (CT). 
### Timeout method

This is the naive method that does not actually eliminate deadlocks, but it still fixes them. The idea is to kill a process and restart it after a given amount of waiting, this is because the system is assuming that a deadlock has occurred, although it cannot be sure. This uncertainty may kill some processes unnecessarily, thus making the system do more work for nothing.
### Wait die algorithm

If RT  $T_{1}$ is older than CT  $T_{2}$, then $T_{1}$ waits, otherwise $T_{1}$ dies.

![[wait die.png]]
### Wound wait

If RT  $T_{1}$ is older than CT  $T_{2}$, then $T_{1}$ wounds $T_{2}$, otherwise $T_{1}$ waits.

![[wound wait.png]]