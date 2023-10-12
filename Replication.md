---
tags:
  - distributed_systems
---
Replication means that we may have more machines to work as a coherent groups, that to the outside observe behave like one singular machine though [[Fault tolerance]]. They offer continuous service and they operate on identical copies of the same state with reaching [[Agreement]].

They usually work with [[Logging]] to ensure that they execute the same command in the same order.
A replicated machine guarantees:
- safety
- availability
### Paxos

Paxos was the reference algorithm for consensus for about 30 years but became obsolete since it's very hard to understand an difficult to implement.
### Raft

Is a new algorithm that requires agreement on single decision and designed to be easily understandable and easy to implement. This is done through the decomposition of problems:
- Log replication: the leader accepts commands from clients and replicates it's log
- Leader election: if the leader crashes, another will take its place
- Safety: only up-to-date server may become leaders