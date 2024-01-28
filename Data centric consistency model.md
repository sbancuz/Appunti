---
tags:
  - distributed_systems
---
In this context we say that a protocol is **highly available** if it does not require synchronous communication so that if a node fails a client can still receive a reply a correct replica. Some consistency models also employ the use of synchronization variables.

>[!tip]
>Also see the part [[Transactions#Controlling concurrency]]
### Sequential consistency

The result is the same as if the operations by all processes were executed in some sequential order, and the operations by each process appear in this sequence in the order specified by its program.

![[data centric consistency.png]]

This means that all the replicas need to agree on a given order of operations: the solution is single leader replication with synchronous replication. Leaderless replication wouldn't work as well since it **wouldn't be highly available**. The main problems will be **high latency** due to the synchronous interactions and the blocking clients in case of a network partition.
#### [[Distributed consistency model#Single leader protocol]] version

All the **write** operation are sent to the leader that, after it receives the change, it propagates the information to all other servers. The **reads** can be done anywhere. The ordering is dictated by the leader.

>[!warning]
>
>Clients are *sticky* -- they can read only from the same replica
#### [[Distributed consistency model#Leaderless protocol]] version

The writes operation operate in a quorum basis on both read and write operations. To keep all the replicas up to date a server must check periodically that all the others are updated, then send the information if needed.
### Linearizable consistency

Each operation should appear to take effect instantaneously at some moment between its start and its completion. The idea is that all the write operations should be immediately visible, but operation should have a duration.

![[linear.png]]

Synchronous single leader replication may implement linearizability but it would be more **difficult to guarantee in the presence of failures**. This would be achieved by locking all the followers and then update the database.
#### [[Distributed consistency model#Single leader protocol]] version

The system will use [[Global clock|vector clock]] to maintain the order of operations and the leader will decide what to commit depending on them. Replicas must be updated asynchronously and most importantly atomically.
### Causal consistency

Writes that are potentially causally related must be seen by all processes in the same order. Concurrent writes may be seen in any order at different machines. This weakens sequential consistency based on Lamport's happens-before relation.

![[causal consistency.png]]
#### [[Distributed consistency model#Multi leader protocol]] version

The system uses [[Global clock|vector clock]] to keep a timestamp that represents what the system knew when it performed a write. An update is applied to a replica only if all possible writes operations that are its possible causes are processed. 
### FIFO consistency

Writes done by a single process are seen by all others in the order in which they were issued; writes from different processes may be seen in any order at different machines. This is also called PRAM consistency.

![[fifo consistency.png]]
#### [[Distributed consistency model#Multi leader protocol]] version

All updates from a process carry a sequence number, a replica can commit this update only after it has received all the updates from the same process with a lower sequence number.