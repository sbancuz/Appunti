---
tags:
  - distributed_systems
---
Consensus protocols are used to communicate through various nodes of a distributed system and ensure a consistent result.

![[FloodSet algorithm]]
### BFT consensus

State machine [[Replication]] can be extended to consider byzantine processes. It follows the same assumptions as raft, but requires $3f+ 1$ participants to tolerate $f$ failing nodes. This is similar to [[Blockchain]]