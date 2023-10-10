---
tags:
  - distributed_systems
---
This method rollbacks the system to a valid checkpoint, but no useless checkpoints are ever taken. With this algorithm we have a coordinator that sends CHKP-REQ, when a receiver receives this request it takes a checkpoint and queues other outgoing messages, when done it sends an ACK to the coordinator.

>[!note]
>Another improvement over this system would be to take incremental snapshots instead of complete snapshots of the system 

