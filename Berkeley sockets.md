---
tags:
  - distributed_systems
---
Sockets are a common abstraction interface for the network stack available on every modern system. Most notably they allow to program with TCP and UDP offering a common API regardless of the communication type.

![[Sockets in C.png]]
### Stream connection

Each connected socket is uniquely identified by 4 numbers:
- IP address server/client
- port server/client
### Datagram connection

Client and server use the same approach to send and receive datagrams. They both create a socket bound to a port and use it to both send and receive datagrams. 
### Multicast connection

It's a network protocol to efficiently deliver UDP datagrams to multiple recipients. This works like a datagram connection.

>[!warning]
>Most routers are configured to not route multicast packets outside the LAN

