---
tags:
  - distributed_systems
---
The advantage of this method for fault recovery is that, starting from a checkpoint, we can replay the actions that are stored in a log file. The method works only if the system is piecewise deterministic.

Each message's header contains all necessary information to replay the messages. Now we divide these messages in 2 groups:
- Stable -> written to stable storage and thus can't be lost
- Unstable 
	- DEP$(m)$ -> processes that depend on the delivery of $m$ 
	- COPY$(m)$ -> processes that have a copy of $m$, but not yet in stable storage

We can define a process as an orphan if there exists $m$ such that it is DEP$(m)$ and all COPY$(m)$ have crashed. In practice there is no way to replay $m$ since it has been lost. These DEP$(m)$ now are useless and we need to delete them.
### Pessimistic logging

These type of protocols ensure that no orphan processes are ever created. We ensure that any unstable message $m$ is delivered to at most one process and the receiver will always be in COPY$(m)$ unless it discards the message and until it gets written to storage the receiver can't send any other message. 
### Optimistic logging

The messages are logged asynchronously, with the assumption that they will be logged before any faults occur. This is achieved by rolling back all the DEP$(m)$ processes to a state in which are no longer in DEP$(m)$.