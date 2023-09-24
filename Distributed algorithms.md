---
tags:
  - distributed_systems
---
Traditional programs can be described in terms of the algorithm they implement where steps are strictly sequential. This is not the case when talking about distributed algorithms that define the steps taken by each process, including the transmission of messages. The behaviour is influenced by:
- the speed of each process
- the performance of the communication channel
- the clock drift rate

### Interaction models

There are 2 types of distributed systems:
- Synchronous : the time to execute each step has known bounds of executions, transmission and clock
- Asynchronous : there isn't any bounds

### Failure model

Both processes and communication channels may fail. The failure model defines the ways in which failure may occur to provide a better understanding of the effects of failures.
We distinguish between:
- Omission failures : crash / can't send / can't receive
- Byzantine failures : omit processing steps / message contents may be corrupted
- Timing failures : (only synchronous) when a time limit is violated

#### Failure detection

Distributed consensus is formally proved to be impossible in an asynchronous system because a message can always be lost. But in reality if we can create a system that can work almost always.

### Layered protocols

![[OSI.png]]

This is achieved with encapsulation of the payload with headers. The middleware includes common services and protocols that can be used by many different applications :
- Marshalling data
- Naming protocols
- Security protocols
- Scaling mechanisms

They also offer different form of communication:
- Transient vs persistent
- Synchronous vs asynchronous

![[synchronization.png]]

### [[RPC]]


