---
tags:
  - distributed_systems
---
The data stored in the distributed system does not update when other nodes are updated. It's used in system where the most common operation is reading and writes appear scarily like [[DNS]] or web caches.
Eventually all the updates are propagated to all the system.

This type of system are very popular today because:
- they are very simple to implement
- there are very few conflicts
- has dedicated conflict free data types (they can store the deltas of operation)

>[!example]
>Say a node updates x from $5$ to $7$ and another from $5$ to $6$, we only store $+1$ and $+2$ so the order of updates doesn't matter


