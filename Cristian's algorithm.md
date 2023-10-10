---
tags:
  - distributed_systems
---
This is a simple algorithm to synchronize clocks in a distributed system.

Periodically each client sends a request to the time server, and messages are assumed to travel fast. The problems with this approach are:
- the time might run backwards on a client machine
- messages are not instantaneous

![[cristian algo.png]]