---
tags:
  - distributed_systems
---
Message oriented communication is centered around the notion of a one-way message, it's usually implemented in a asynchronous manner with both persistency and multi-point interaction in mind.

![[messages.png]]
### Transport protocols

The well-known protocols that implement this interface are:
- TCP
- UDP

To use them we need to program with [[Berkeley sockets]] or [[MPI]].
### Message queuing

It's a point-to-point persistent asynchronous communication, intrinsically [[P2P]]. It works by creating queues that send and receive messages. In principle it's like how e-mail works.

![[messageQ.png]]

In [[Client server]] application, message queuing functions by asynchronously fetching requests from the queue and then responding to the clients' queue. In this way the client doesn't know how many servers handle the requests, it only cares about the response. It's a nice way to implement a sort of load balancing.