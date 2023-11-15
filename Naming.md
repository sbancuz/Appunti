---
tags:
  - distributed_systems
---
Names are used to refer to entities and are typically accessed through an access points. Using IP addresses is not convenient to refer to a machine, it's better to use a name and some type of server that translates names to addresses. 

A **global name** denotes the same entity, no matter where the name is used, a **local name** entity is dependent on the location of the node. Resolving names directly into addresses doesn't work well with mobility, to resolve this we use **identifiers**. These are names that we are sure that they are unique and never change and help with [[Name resolution]].

A name can be either:
- Human friendly
- Machine friendly

The problem with naming system is to remove unused and unwanted entities. This is exactly the same problem as a [[Garbage collector]].