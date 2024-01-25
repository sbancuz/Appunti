---
tags:
  - distributed_systems
---
Many distributed systems require a process to act as a coordinator to all the others, but if this process crashes the system must elect a new one to act as such. This process must ensure that the [[Logging]] be replicated in a correct manner to ensure minimal to no rollback.

> [!warning] Assumptions
For this algorithms to work we need that processes to be divided in groups, with only one node that acts as a leader and each node has to have an **unique id**. We also need reliable connection for this system to work since each message is on a timer and also the problem of finding out the node that has crashed has to be decidable.
### Bully election algorithm

When a process $P$ notices that a leader is unresponsive, it sends an ELECT it's ID to other processes with higher ID than its own and waits for a response. If none respond then $P$ will be automatically promoted to a leader and sends a COORD notice to the processes with lower IDs. If a process $P'$ receives and ELECT it responds and starts a new election.
### Ring based algorithm

We assume a logical ring in the nodes and when a process detects a leader failure, it sends an ELECT message containing its ID and all the previous ones to the closest alive neighbor and waits for an OK response, if it doesn't happen then it tries with the next one. If $P$ is in the list then the type of message will be COORD. Upon receiving a COORD a node considers the process with the highest ID as the new leader.