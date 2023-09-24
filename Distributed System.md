---
tags:
  - distributed_systems
---
A distributed system is a collection of independent computers that appears to its users as a single coherent system.

>[!info] best definition
>One on which I cannot get any work done because some machine I have never heard of has crashed --L. Lamport

![[DS.png]]

The defining features of a distributed system are:
- concurrency
- absence of a global clock : you **cannot** use the computer physical clock for the purpose to synchronize systems
- Independent failures

--> [[Modeling a distributed system]]
--> [[Distributed algorithms]]
### Biggest problems

##### Heterogeneity

- Networks : Even when TCP/IP hides most of the networking differences, the ones ate the ISO/OSI layers 1,2 must be considered
- Computer hardware : Data representation may vary with the hardware platform
- OS : The API provided to access TCP/IP may vary
- Programming languages : Different languages represent data structures differently

#### Openness

It determines whether a system can be extended and re-implemented in various ways through the adoption of protocols and standards of communication.

#### Security

Security for the information resources made available and maintained has three components:
- Confidentiality
- Integrity
- Availability

#### Scalability

The ability of a system to increase size with some points of centralization like databases and decentralized algorithms for caching and asynchronous communication.

#### Failure handling

A system may fail partially so we need to:
- detect failures
- masking failures
- tolerating failures
- recovering from them
- add redundancy

#### Concurrency

Managing the access to shared resources must be carefully synchronized

#### Transparency

A system must hide the fact the everything could change, could have copies or has failed from the end user.