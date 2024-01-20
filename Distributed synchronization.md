---
tags:
  - distributed_systems
---
The problem of synchronization doesn't appear only in distributed systems, but when it does, it makes things a lot more complicated. The problem is that every clock in every machine will be out of sync so we need to maintain a sort of [[Global clock]].
### Mutual exclusion

It's a system that prevents interference and ensures [[Distributed consistency model|consistency]] of resources access. And it requires:
- Safety property
- Liveness property
- Happens-before relationship

The simplest solution is to manage the shared resource with only one server and handle access with tokens. Printers utilize this model because it's easy to implement and to use.

There are two types of locks:
- r_lock $\to$ shared
- w_lock $\to$ exclusive
#### [[Global clock|Scalar clock]]

With this approach we can also use  scalar clocks to ensure the orderness of the messages . This has the advantages of having the possibility to implement a wait queue to acknowledge all the requests and removing the single point of failure that was the centralized server.
#### Token ring

Another approach is using a token ring solution, all processes are organized in a logical ring that keeps passing a token and this token grants access to the shared resource.
#### [[Transactions]]
### Global state

The global state represents the local state of every process in a distributed system together with the messages in transit over the links. A global state can be useful for debugging, [[Termination and deadlock detection]]. Though this would need a [[Global clock]]. A global state can be approximated with the use of cuts that represent the state of all the process and their history up to a certain event. This is called [[Logging]].