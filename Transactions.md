---
tags:
  - distributed_systems
---
A transaction is  an elementary, atomic unit of work performed by an application, in case of a DBMS system they are used as 

Transactions are a method to protect a shared resource against simultaneous access by several processes. Transactions are a sequence of operations that define appropriate programming primitives:
- BEGIN_TRANSACTION
- END_TRANSACTION
- ABORT_TRANSACTION
- READ
- WRITE

There exists several transaction types:
- [[ACID]]
- Nested -> Constructed from several sub-transaction
- Distributed
### Atomicity

Atomicity can be achieved with either a private workspace that copies the memory in a shadow region and operates on that or with a writeahead [[Logging]]
### Controlling concurrency

This can be achieved through separation of concerns. This scheduler must ensure that operations must interweave correctly.

![[conc trans.png]]

To ensure sequentiality of instruction we use 2 phase locking. The scheduler test if a resource has already received a lock, if so, the operation is delayed. Once a lock for $T$ has been released, $T$ can no longer acquire it. It may deadlock. Another approach to achieve seriability is [[Pessimistic timestamp ordering]] or [[Optimistic timestamp ordering]]


Vedere anche [[transazioni]] di sistemi informativi, magari si possono mettere assieme.
=