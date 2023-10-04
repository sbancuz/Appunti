---
tags:
  - distributed_systems
---
Names are organized in a name space, in some case this space is a labeled graph composed of leaf and directory nodes. A leaf represents a named entity and a directory a number of a label that points to different nodes in the graph. 

Resources are referred through path names that can be either absolute or relative.
An example of this can be the file system on the computer.
### Name space distribution

Name spaces for a large scale distributed system are often distributed among different name servers which are usually organized hierarchically. This space is partitioned into layers:
- Global level -> high level directories which main purpose is to manage administrations
- Administratorial level -> contains mid level directory node that can be grouped in such a way that each group can be assigned to a separate administration
- Managerial level -> low level directories within a single administration and it maps nodes to local name servers

![[name space.png]]

An example of structured named system is the [[DNS]]