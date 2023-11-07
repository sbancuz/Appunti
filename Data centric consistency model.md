---
tags:
  - distributed_systems
---
In this context we say that a protocol is highly available if it does not require synchronous communication so that if a node fails a client can still receive a reply a correct replica. Some consistency models also employ the use of synchronization variables.
### Sequential consistency

The result is the same as if the operations by all processes were executed in some sequential order, and the operations by each process appear in this sequence in the order specified by its program.

![[data centric consistency.png]]

This means that all the replicas need to agree on a given order of operations: the solution is single leader replication with synchronous replication. Leaderless replication wouldn't work as well since it wouldn't be highly available. The main problems will be high latency due to the synchronous interactions and the blocking clients in case of a network partition.
### Linearizable consistency

Each operation should appear to take effect instantaneously at some moment between its start and its completion. The idea is that all the write operations should be immediately visible, but operation should have a duration.

![[linear.png]]

Synchronous single leader replication may implement linearizability but it would be more difficult to guarantee in the presence of failures. This would be achieved by locking all the followers and then update the database.
### Causal consistency

Writes that are potentially causally related must be seen by all processes in the same order. Concurrent writes may be seen in any order at different machines. This weakens sequential consistency based on Lamport's happens-before relation.

![[causal consistency.png]]
### FIFO consistency

Writes done by a single process are seen by all others in the order in which they were issued; writes from different processes may be seen in any order at different machines. This is also called PRAM consistency.

![[fifo consistency.png]]

