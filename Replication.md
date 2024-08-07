---
tags:
  - distributed_systems
---
Replication means that we may have more machines to work as a coherent groups, that to the outside observe behave like one singular machine though [[Fault tolerance]]. They offer continuous service and they operate on identical copies of the same state with reaching [[Agreement]]. Another reason to use replication is [[Availability]], so data locality of the data. 

They usually work with [[Logging]] to ensure that they execute the same command in the same order.
A replicated machine guarantees:
- safety
- [[availability]]
### Paxos

Paxos was the reference algorithm for consensus for about 30 years but became obsolete since it's very hard to understand an difficult to implement.
### Raft

Is a new algorithm that requires agreement on single decision and designed to be easily understandable and easy to implement. This is done through the decomposition of problems:
- Log replication: the leader accepts commands from clients and replicates it's log
- [[Leader election]]: if the leader crashes, another will take its place
- Safety: only up-to-date server may become leaders

The result of any operation is what the majority of the machine return.  

Crashes may result in log inconsistencies, in this case the leaders' log is considered the only point of truth in the systems and gets replicated to all the other servers. 
#### Log matching property

This property is guaranteed in raft through an header in the message that contains a pair of index and term of any entry preceding the new ones.

If log entries on different servers have the same index and term:
- they store the same command
- they are equal in all preceding entries

If a given entry is committed, all preceding ones are also committed. 

