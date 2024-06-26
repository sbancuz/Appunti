---
tags:
  - distributed_systems
---
Traditional programs can be described in terms of the algorithm they implement where steps are strictly sequential. This is not the case when talking about distributed algorithms that define the steps taken by each process, including the transmission of messages. The behavior is influenced by:
- the speed of each process
- the performance of the communication channel
- the clock drift rate
### Interaction models

There are 2 types of distributed systems:
- Synchronous : the time to execute each step has known bounds of executions, transmission and clock (just theoretical)
- Asynchronous : there isn't any bounds
### ([[Fault tolerance]])
### Layered protocols

![[OSI.png]]

This is achieved with encapsulation of the payload with headers. The middleware includes common services and protocols that can be used by many different applications :
- Marshalling data
- [[Naming]]
- Security protocols
- Scaling mechanisms e.g. [[Replication]]

They also offer different form of communication:
- Transient vs persistent
- Synchronous vs asynchronous

![[synchronization.png]]
