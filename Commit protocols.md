---
tags:
  - distributed_systems
---

The commit protocols ensure atomicity in a distributed system. This is done through atomic commits. When using atomic operations we ensure that either all nodes commit or all nodes abort. This can be achieved either through 2 Phase Commit or 3 Phase commit. In practice the 3PC is more robust but it is more expensive and thus not really used.
### 2PC

This protocol works through timeouts, in fact after a acknowledging a timeout the coordinator assumes a failure. In case the coordinator fails in an operation nothing will ever be committed, but if the coordinator fails when everybody is in the ready state the process will block until the coordinator recovers.

![[2pc.png]]

>[!note]
>The coordinator is also a participant, it just acts also as a coordinator
#### 3PC

The 3PC is an attempt to solve the problems of 2PC by adding another phase to the protocol, this will make the 3PC non-blocking. The idea is to split the commit:
- Communicate the outcome to all the nodes
- Commit only after everyone knows the outcome

![[3pc.png]]

If a participant fails it behaves just like the 2PC, but if the coordinator fails:
- Waiting participants can decide to abort
- Ready participant can contact other participant and decide whether to commit or abort on their own
- No 2 participant can be one in pre-commit and the other in init
