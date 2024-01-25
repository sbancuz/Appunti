---
tags:
  - distributed_systems
---
### Describe the REST architectural style

The REST style is s way to build a client server application that communicates under HTTP/HTTPS via JSON messages. This is because REST only offers four methods for communication: PUT, POST, GET, DELETE; thus there isn't enough methods to build an entire application. The solution to this problem is to encode the signature and arguments of a function is a JSON message and send that through one of the four methods listed before. The other main point of REST is that only the client should hold the state of the connection, thus the server shall have no such concept. In reality a pure REST application is hard to implement and wouldn't really meet the needs of the users, for this reason usually the server will hold some information of the client in persistent storage like a database.

All the responses that the client receives can be specified to be cached.
### Describe name resolution in general and focus on the various approaches you know to resolve flat names.

Names are used to refer to entities in a syst
