---
tags:
  - distributed_systems
aliases:
  - consistency
  - Consistency
---
A consistency model is a contract between the processes and the data store that can guarantee either performance or reliability for the system. ---> [[CAP theorem]]

![[consistency.png]]

Different models will have different guarantees and different protocols that implement them:
- Guarantees on content -> max difference on the versions stored at different replicas
- Guarantees on staleness -> max time between a a change and its propagation for the replicas
- Guarantees on the order of updates -> constraints on behaviour in case of conflicts
### Single leader protocol

One of the replicas will be appointed as leader and, when other clients want to write to a datastore,  clients must send a request to the leader which writes it first to its local storage and then propagates it. 
The other replicas are known as followers.

When a clients wants to read from the database they can query it from the any replica they want.

In this protocol the operation can either be:
- Synchronous -> The write completes after the leader has received a reply from all the followers
- Asynchronous -> The write completes when the new value is stored on the leader
- Semi-synchronous -> The write completes when a leader receives a reply from some $k$ followers

In case of failure we can just elect a new leader. Also write-write conflicts are not possible since the leader decides on the order of all the write operations. These types of protocols are generally adopted in data centers with data bases.
### Multi leader protocol

Write are carried out at different replicas concurrently, no single leader means we can't decide on the order of the writes. This protocol is primarily used in geographically distributed applications like social networks where conflicts are not critical and writes are not frequent.
### Leaderless protocol

To have the latest changes the client has to contact multiple replicas to perform both read and writes. 

>[!note]
>In some implementations a coordinator forwards operations to replicas on behalf of the client

Leaderless uses a quorum-based protocol to avoid conflicts similar to a voting system.
### Data centric consistency model

In this context we say that a protocol is highly available if it does not require synchronous communication so that if a node fails a client can still receive a reply a correct replica.
#### Sequential consistency

The result is the same as if the operations by all processes were executed in some sequential order, and the operations by each process appear in this sequence in the order specified by its program.

![[data centric consistency.png]]

This means that all the replicas need to agree on a given order of operations: the solution is single leader replication with synchronous replication. Leaderless replication wouldn't work as well since it wouldn't be highly available. The main problems will be high latency due to the synchronous interactions and the blocking clients in case of a network partition.
#### Linearizability

Each operation should appear to take effect instantaneously at some moment between its start and its completion. The idea is that all the write operations should be immediately visible, but operation should have a duration.

![[linear.png]]

Synchronous single leader replication may implement linearizability but it would be more difficult to guarantee in the presence of failures. This would be achieved by locking all the followers and then update the database.
### Causal consistency

Writes that are potentially causally related must be seen by all processes in the same order. Concurrent writes may be seen in any order at different machines. This weakens sequential consistency based on Lamport's happens-before relation.

![[causal consistency.png]]