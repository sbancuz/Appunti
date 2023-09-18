---
tags:
  - distributed_systems
  - sistemi_informativi
---
REpresentational State Transfer, is a set of principles that define how Web standards are supposed to be used. It's interaction use [[Client server]] approach and are stateless. **The state must be transferred from clients to servers**. The data received from the response should specify if is cacheable or not. The data is transferred through HTTP

The problem is that HTTP has only 4 methods:
- PUT
- POST
- GET
- DELETE

But these are not enough to represent every function that a server must handle. To resolve this problem we encode as in string representation both the signature of the function to call and the data needed for the call. This textual representation can be JSON, XML or something else. 
#### Key Goals

- Scalability
- Generality of interfaces
- Independent deployment of components
- Intermediary components to reduce latency

#### Uniform interface constraints

The uniform interface exposed by components must satisfy 4 constraints:
- Identification of resources: through URI or ID
- Manipulation of resources through representations
- Self descriptive messages
- Hypermedia as the engine application state