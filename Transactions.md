---
tags:
  - distributed_systems
---
A transaction is  an elementary, atomic unit of work performed by an application, in case of a DBMS system they are used as a method to protect a shared resource against simultaneous access by several processes. Transactions are a sequence of operations that define appropriate programming primitives:
- BEGIN_TRANSACTION
- END_TRANSACTION $\to$ commit-work
- ABORT_TRANSACTION $\to$ rollback-work
- READ
- WRITE

There exists several transaction types:
- [[ACID]]
- Nested -> Constructed from several sub-transaction
- Distributed
### Atomicity

To ensure that atomicity is respected only the after the **commit** the changes will take effect in the actual DBMS and in all other cases the system will issue a **rollback** to restore the state of the system like it was before the operation.  This can be achieved with either a private workspace that copies the memory in a shadow region and operates on that or with a writeahead [[Logging]]. 
### Consistency

A transaction must satisfy the DB integrity constraints
- if $S_{0}$ is consistent then $S_{f}$ is also consistent
- this is not guaranteed for the intermediate states
### Isolation

The execution of a transaction must be independent of the concurrent execution of other transactions, in particular, the concurrent execution of a number of transaction must produce the same result as if they were executed sequentially.
### Durability

The effect of the successful transaction will be committed and will last **forever**.
### Controlling concurrency

This can be achieved through separation of concerns. This scheduler must ensure that operations must interweave correctly and respect the [[Data centric consistency model]]. If this isn't the case there are 5 types of anomalies that can happen:
- lost update $\to$ update is applied from a state that ignores preceding update $r_{1}-r_{2}-w_{2}-w_{1}$ 
- dirty read $\to$ uncommitted data is used to update data $r_{1}-w_{1}-r_{2}-ab_{1}-w_{2}$
- non repeatable read $\to$ someone else updates a previously read value $r_{1}-r_{2}-w_{2}-r_{1}$
- phantom update $\to$ someone else updates data the contributes to a constraint $r_{1}-r_{2}-w_{2}-r_{1}$
- phantom insert $\to$ someone else inserts data that contributes to previously read data $r_{1}-w_{2}-r_{1}$

![[conc trans.png]]

We can define an **operation** as a read/write operation of a specific datum by a transaction and are specified by
$$
\{r/w\}_{PID}(var)
$$
A **schedule** is a sequence of operations performed by concurrent transactions that respects the order of operation of each transaction. To check if a non serial schedule is admissible we have to define the notion of correctness -- that is a schedule that leaves the database in the same state as some serial schedule of the same transaction.
#### View serializability

Two schedules are **view-equivalent** if they have
- the same operation
- same reads-from relationship $\to$ $W_{j}(x)$ precedes $R_{i}(x)$ and there is no $W_{k}(x)$ in between
- the same final writes $\to$ $W_{i}(x)$ is the last write on $x$ that occurs in $S$

Deciding view-equivalence of two given schedules is done in polynomial time and space [[Complexity of an algorithm]], but the problem of deciding if a generic schedule is can be view serializable is NP complete.
#### Conflict serializability

This technique defines the order of operation by dealing with conflicts. Two operations $o_{i} \neq o_{j}$ are in **conflict** if they address the same resource and at least one of them is a write. So there can be just two types
- read write
- write write

Two schedules are **conflict equivalent** if they contain the same operations and in all the conflicting pairs the transactions occur in the same order. Also a schedule is **conflict serializable** iff it is conflict equivalent to a serial schedule of the same transactions. 

To ensure sequentiality of instruction we use 2 phase locking. The scheduler test if a resource has already received a lock, if so, the operation is delayed. Once a lock for $T$ has been released, $T$ can no longer acquire it. It may deadlock. Another approach to achieve seriability is [[Pessimistic timestamp ordering]] or [[Optimistic timestamp ordering]].

>[!tip]
>All conflict serializable schedules are also view serializable

Testing for conflict serializability is way easier than view serializability, because we can use a conflict [[graphs]] that has 
- one node foe each transaction
- one arch from $T_{i} \to T_{j}$ if there exists at least one conflict between $o_{i}\in T_{i}$ and $o_{j }\in T_{J}$
If the graph is acyclic, then the schedule it's conflict serializable.

We can check if a schedule is VSR if, after building the dependency graph and checking that is not CSR,  we remove the **blind write** -- that is a write $W_{i}(x)$ that is not the last action of $x$ and the following action is a write -- conflicts and see if the resulting graph is acyclic.



Vedere anche [[transazioni]] di sistemi informativi, magari si possono mettere assieme.
=