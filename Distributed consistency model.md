---
tags:
  - distributed_systems
aliases:
  - consistency
  - Consistency
---
A consistency model is a contract between the processes and the data store that can guarantee either performance or reliability for the system. ---> [[CAP theorem]]

![[consistency.png]]

The problem that consistency models solve is to maintain updated all the [[Replication|replicas]] of a given system.

Different models will have different guarantees and different protocols that implement them:
- Guarantees on content -> max difference on the versions stored at different replicas
- Guarantees on staleness -> max time between a a change and its propagation for the replicas
- Guarantees on the order of updates -> constraints on behavior in case of conflicts

These models are implemented though:
- [[Data centric consistency model]]
- [[Eventual consistency model]]
- [[Client centric consistency model]]
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
