---
tags:
  - distributed_systems
---
This consists in periodically saving the distributed state of the system to stable storage.

![[checkpointing.png]]

The most trivial solution is to have each process independently record its own state, this is not idea because we may need to rollback to a set of checkpoints which result in a consistent cut and it may lead to a domino effect. Fortunately this is not the only method, we can tag the interval between 2 checkpoints and each message has to be labelled with a reference of the interval. 
When a failure occurs the recovering process broadcasts a dependency request to collect information stopping all processes in the process. The recovery line can be computed with:
 - [[Rollback dependency graph]]
 - [[Checkpoint graph]]