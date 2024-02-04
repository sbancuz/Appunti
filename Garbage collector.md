---
tags:
  - distributed_systems
  - coding
---
The aim of a garbage collector is to scan for unused part of nodes that we can remove from the system. In case of a programming language this nodes may represent variables and memory, in case of a distributed system this may be the entities on a network.
### Mark and Sweep

This algorithm traverses the graph and marks every node that has encountered. After it's done visiting all the nodes that it can, it scans for nodes that have not been visited and it removes them from the system. Only this approach can find unreferenced parts of the entities that are in a group, but this is never done on a large scale because it needs to halt the system to do those checks. 
### Reference counting

The object keeps track of how many other objects have been given references, if this number goes to $0$ then we know that we can safely remove it. This is not safe in a distributed system since deleting an entity is a race condition. This could be solved by using acknowledges, but it does not scale well.

![[refcount.png]]
### Weighted reference counting

This approach tries to solve the problems of reference counting by only keeping track of the decrements. When a node is initialized it has two counters to the same number
- Total weight $\to$ it never changes
- Partial weight $\to$ it can change

When creating a new reference half of the partial weight gets sent to the other node and when it gets deleted it will give back the borrowed weight. We can define that a node has finished its computation when the total weight becomes equal to the partial weight. This approach has clear limitations on how many nodes can be connected to another, this problem can be circumvented by simply creating new skeletons -- i.e. a new computation, thus creating a layer of indirection, and acting as a proxy.
### Reference listing

Instead of keeping track of the number of references, keep track of the identities of the proxies. This has the advantage that insertion and deletion of a proxy is idempotent and is easier to maintain. Though this method still suffers from race conditions. It keeps checking if an entities are still alive through pings.