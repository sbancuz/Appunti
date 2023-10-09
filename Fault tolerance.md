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
- Agreement -> no 2 processes decide on different values
- Validity -> $v$ is the only possible decision value
- Termination -> All non-faulty processes eventually decide

![[FloodSet algorithm]]

On the other hand an algorithm that can handle also byzantine failures needs to have these properties:
- Agreement -> No 2 non-faulty processes decide on different values
- Validity -> If all non-faulty processes start with a starting value $v$, then $v$ is the only possible decision value
- Termination -> all non-faulty processes eventually decide