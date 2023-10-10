---
tags:
  - distributed_systems
---
The problem of synchronization doesn't appear only in distributed systems, but when it does, it makes things a lot more complicated. The problem is that every clock in every machine will be out of sync so we need to maintain a sort of global clock.
### Physical time

Computer clocks are not clocks per se, they are timers, so depending on the drift rate of the clock they could go out of sync. To resolve this we can either:
- Synchronize all clocks against a single one
- Synchronize all clocks among themselves

![[Cristian's algorithm]]

![[Berkley algorithm]]
![[NTP]]
### Logical time

In logical time we only care about the order of operation and the causality of the relationships of the events, not the exact time of the recording. 
#### Scalar clock

Lamport defined the **happens-before** relationship which means that if 2 events happen in the same process then one must happen before the other. If this does not hold then they are **concurrent**. This provides the best approximation of causality in a system.

The idea is that each process, keeps a logical scalar clock that it gets incremented each time a message is sent. If a message is received the clock is set to $\max(\text{msgtime}, \text{clock})$. 

![[logic clock.png]]

To achieve total ordering we can attach the process ID to the clocks.
### Vector clock

Scalar clocks do not actually represent correctly the happens-before relationship, to fix this we use vector clocks that maintain a vector of timers such that $V_{i}[i]$ is the number of events occurred in the $P_{i}$

We define:
- $V=V'$ iff $V[i] = V'[i],  \forall {i}  {}$ 
- $V\leq V'$ iff $V[i] \leq V'[i],  \forall {i}  {}$ 
- $V<V'$ iff $V \leq V' \land  V \neq V'$ 
- $V || V'$ iff $\lnot(V < V') \land \lnot(V'<V)$ 

