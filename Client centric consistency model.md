---
tags:
  - distributed_systems
---
This model is for the type of clients that can dynamically switch the replicas that it is connected to. To implement such system we need:
- unique identifier to each operation -> replica id + sequence number
- Read set
- Write set

The read/write identifiers can be encoded as [[Global clock|vector clock]]
### Monotonic reads

If a process reads the value of a data item $x$, any successive read operation on $x$ by that process will always return that same value or a more recent value.

![[client centric.png]]
### Monotonic writes

A write operation by a process on a data item $x$ is completed before any successive write operation on $x$ by the same process. This is similar to FIFO consistency, but ordering does not matter.

![[monotic writes.png]]
### Read your writes

The effect of a write operation by a process on a data item $x$ will always be seen a by a successive read operation on $x$ by the same process.

![[read your writes.png]]
### Writes follow reads

A write operation by a process on a data item $x$ following a previous read operation on $x$ by the same process is  guaranteed to take place on the same or more recent value of $x$ that was read

![[write follows read.png]]