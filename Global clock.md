---
tags:
  - distributed_systems
aliases:
  - scalar clock
  - vector clock
---
*A* true global clock only exists inside a single machine, it cannot be implemented in a distributed system. Though since it's integral to their existences there exists several approximations.
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
#### Vector clock

Scalar clocks do not actually represent correctly the happens-before relationship, to fix this we use vector clocks that maintain a vector of timers such that $V_{i}[i]$ is the number of events occurred in the $P_{i}$

We define:
- $V=V'$ iff $V[i] = V'[i],  \forall {i}  {}$ 
- $V\leq V'$ iff $V[i] \leq V'[i],  \forall {i}  {}$ 
- $V<V'$ iff $V \leq V' \land  V \neq V'$ 
- $V || V'$ iff $\lnot(V < V') \land \lnot(V'<V)$ 

If a reply arrives before it's message/request, the system will delay it's acceptance until it receives the message. This is done by looking the other vector clocks contained in the message.

>[!example]-
> For example if it sees that $P_{1}$ sent a message to $P_{2}$ and $P_{2}$ sends its response to $P_{3}$, $P_{3}$ will not accept the message from $P_{2}$ until it receives the one from $P_{1}$. And it knows that there exist a message sent from $P_{1}$ just by looking at the vector clock in the message received from $P_{2}$ since it will be $(z+ 1,x + 1,y)$ and in $P_{3}$ we will hold $(z, x, y)$
> 
> ![[vec clocks.png]]

Causal delivery is an extension of the normal vector clock functionality that can be implemented by incrementing the clock value only when the message is being accepted and not when it's received. If a process receives a message before it can actually be processed, it delays its acceptance util the previous message is accepted and processed.

![[vector ordered clokc.png]]