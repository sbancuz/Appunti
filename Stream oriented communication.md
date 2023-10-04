---
tags:
  - distributed_systems
---
A stream oriented communication works with [[Data streams]] and can be:
- synchronous -> the is a max end-to-end delay for each unit in the data stream
- asynchronous -> The items in a stream are transmitted one after the other
- isosynchrnous -> There is max/min end-to-end delay 

![[stream.png]]

Non functional requirements are often referred to as **Quality of Service**. 

The header of a stream packet contains an 8-bit field that encodes
- 6 bits for the Differentiated Services Code Point, this encodes the Per Hop Behaviour
- 2 bits for the Explicit Congestion Notification

### Enforce QoS at the application layer

![[QoS.png]]

It's recommended to use both buffering and interleaving data to mitigate data loss and improve QoS 
