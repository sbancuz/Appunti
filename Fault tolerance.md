---
tags:
  - distributed_systems
---
Fault tolerance is needed to build a dependable system that can be described as both available most of the time and reliable

>[!warning]
>If a system goes down for one millisecond every hour, it's highly available but also highly unreliable

We can also define a failure as the result of an error in the system that itself is caused by a fault. Faults can be also classified as:
- Transient -> occur once and disappear
- Intermittent -> appear and vanish with no apparent reason
- Permanent -> continue to exist until the failed components are repaired
### Failure types in DS

Both processes and communication channels may fail. The failure model defines the ways in which failure may occur to provide a better understanding of the effects of failures.
We distinguish between:
- Omission failures : crash / can't send / can't receive
- Byzantine failures : omit processing steps / message contents may be corrupted
- Timing failures : (only synchronous) when a time limit is violated
#### Failure detection

Distributed consensus is formally proved to be impossible in an asynchronous system because a message can always be lost. But in reality if we can create a system that can work almost always.

In practice we can assume bounds of execution so large that it would never cause problems.
### Masking a failure

The general technique for masking a failure is redundancy:
- Information redundancy -> hamming codes, ECC, ...
- Time redundancy -> try again
- Physical redundancy -> multiple machines
### Process resilience

Redundancy can be used o mask the presence of faulty processes, with redundant process groups the work that can be done by a group of processes can be taken care of by multiple instances and when a process fails it doesn't have any impact on healthy processes. This method can be implemented in 2 methods:

![[process group.png]]

Having a group coordinator is "easy" but it's always a single point of failure.

The size of the group depend on the types of failure that can occur to the group, let's consider a replicated-write system: information is stored by a set of replicated processes so $k + 1$ processes allow the system to be $k$-fault tolerant. But if the failures are byzantine then we need $2k + 1$ processes.

In this method the failures are dealt with a majority of consensus approach, if the processes are deterministic, when all the processes finish executing the result will be the agreement dictated by all non faulty processes.

All algorithms that detect crash failures must have these properties:
- [[Agreement]] -> no 2 processes decide on different values
- Validity -> $v$ is the only possible decision value
- Termination -> All non-faulty processes eventually decide

On the other hand an algorithm that can handle also byzantine failures needs to have these properties:
- [[Agreement]] -> No 2 non-faulty processes decide on different values
- Validity -> If all non-faulty processes start with a starting value $v$, then $v$ is the only possible decision value
- Termination -> all non-faulty processes eventually decide
#### Reliable group communication multicast

The idea with this approach is to exploit process resilience by means of [[Replication]]. In this approach groups are fixed and process must be non-faulty. In case of a multicast failure the receiver must send 
back a NACK. The problem here is that there must be an [[Agreement]] about who is in the group and that the receiver must be able to infer if a packet is missing.

![[non rel comm.png]]
#### Hierarchical feedback control

Receivers are organized in groups headed by a coordinator and groups are organized in a tree routed at the sender.

![[hie feedback control.png]]

### Synchrony

Ideally we would like:
- any 2 processes that receive the same multicast message to see the corresponding events in the same order
- multicast will be delivered to all the members of the group

Unfortunately this can't be the case, thus we need a mechanism to detect these types of failures, and even if we can detect failures correctly, we cannot know whether a failed process has received and processed a message. To resolve this we implement a form of virtual synchrony. With virtual synchrony a group view is the set of processes to which a message should be delivered as seen by the sender at the sending time and also all group view changes must be delivered in a consistent order with respect to other multicasts and each other. We say that a view change occurs when a process joins or leaves the group.

![[Virtual sync.png]]

Retaining the virtual synchrony property, we can identify different orderings for the multicast messages: 
- Unordered multicasts
- FIFO
- Causally-ordered multicast

>[!warning]
>No matter the ordering chosen, we must guarantee that messages must be delivered to every group member in the same order
#### Atomic multicast

Atomic multicast is defined as a virtually synchronous reliable multicast offering totally ordered delivery of messages.
### Recovering

When a process resumes its work after a failure, they have to be taken back to a correct state:
- Backward recovery -> the system is brought back to a previously saved correct state
- Forward recovery -> the system is brought into a new correct state from which execution can be resumed

This can be achieved through:
- [[Checkpointing]]
- [[Logging]]