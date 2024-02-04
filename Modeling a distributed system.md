---
tags:
  - distributed_systems
---
### Software architecture

The architecture of a distributed system can be either:
- Network OS based : the OS provides the communication services
- [[Middleware]] based : the middleware provides communication, coordination and administration masking the OS
#### Runtime

It identifies the classes of components that build the system, the various types of connectors, and the data type exchanged. Modern distributed systems adopts one of these architectural styles:
- [[Client server]] (Most common)
- [[Service oriented]]
- [[REST]]
- [[Peer to peer]]
- [[Object-oriented distributed system]]
- [[Data centered model communication]]
- [[Event based]]
- [[Mobile code]]
### Communication

The nodes in a distributed system are represented with [[Naming]].
The communication in a distributed system can be implemented with [[Distributed algorithms]] in:
- [[Message oriented communication]]
- [[RPC]]
- [[Stream oriented communication]]

![[CAP theorem]]