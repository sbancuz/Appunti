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
- [[P2P]]
- [[Object-oriented distributed system]]
- [[Data centered]]
- [[Event based]]
- [[Mobile code]]
### Communication

The communication in a distributed system can be implemented in:
- [[Message oriented communication]]
- [[RPC]]
- [[Stream oriented communication]]

### Naming

Names are used to refer to entities and are typically accessed through an access points. Using IP addresses is not convenient to refer to a machine, it's better to use a name and some type of server that translates names to addresses. 

A **global name** denotes the same entity, no matter where the name is used, a **local name** entity is dependent on the location of the node. Resolving names directly into addresses doesn't work well with mobility, to resolve this we use **identifiers**. These are names that we are sure that they are unique and never change and help with [[Name resolution]].
