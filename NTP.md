---
tags:
  - distributed_systems
---
Designed for UTC to sync over large-scale networks. It applies hierarchical [[Distributed synchronization]] through means of daemons running on the computer and keeping the machine in sync.  

It becomes a tree structure with the nodes on the top that are synchronized with atomic clocks, and all the nodes below that are kept in sync with the one on the top. In LANs we use multicast to signal the clock to all the nodes in the network. When a link is longer we can use procedure-call and symmetric mode.

![[NTP.png]]

This last approach is used to estimate the offset of clock B relative to clock A, and also measure the accuracy of this estimate.

![[NTP-Algorithm.svg.png]]

The time offset represents the difference of absolute time between the client and the server
$$
\theta = \frac{(t_{1}-t_{0}) + (t_{2}-t_{3})}{2}
$$
Also the round trip delay is defined as
$$
\delta = (t_{3}-t_{0}) = (t_{2} - t_{1})
$$