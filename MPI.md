---
tags:
  - distributed_systems
---
In high performance networks we need higher level primitives for asynchronous, transient communication. It's a network API more higher level than [[Berkeley sockets]] and provides more ease of use.
### Communication

The communication takes place within a known group of processes and within each group is assigned a pair of **(groupID, processID)**  that represents the connection.

>[!warning]
>There is no support for fault tolerance

