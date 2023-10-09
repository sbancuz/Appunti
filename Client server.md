---
tags:
  - distributed_systems
---
Components have different roles and provide a well defined API to access its services.
#### Tiers

Often servers operate by taking advantage of the services offered by other components. So an application can be partitioned by 3 classes:
- UI
- Application services
- Storage services

>[!warning]
>There can be an infinite amount of tiers, it depends on the needs of the application

![[Ntiers.png]]

### [[Fault tolerance]] 

Reliable point-to-point communication is usually provided by TCP, which masks omission failures using acks and retrasmissions. The benign cases of a crash are, these can be easily managed:
- the client can't find the server
- client request is lost

However, system crashes are not so easy to mask. The problem is that the client cannot tell in which part of the handling of the request the server crashed. Similar problems occur when the reply from the server is lost.
- Was the reply lost?
- The request did not arrive?

>[!warning]
Some request may not be idempotent, so resending the request may not always be an option  

Another issue is the client crashing. A computation started by a dead client is called an orphan. The problem is that orphans still consumer resources on the server and the server must get rid of them:
- Extermination
- Reincarnation -> kill old computation with a reconnection
- Gentle reincarnation -> kill only if owner cannot be located
- Expiration -> clients wait to reboot to let remote computation expire