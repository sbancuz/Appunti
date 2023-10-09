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

