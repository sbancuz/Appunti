---
tags:
  - databases
---
The architecture of a database can be divided in two parts:
- The [[Physical database]] that handles how information is stored in the system
- The logical part that handles the retrieval of the information

![[query management.png]]

The **Query manager** handles the [[Query optimization]] step of execution that reduces the number of I/O operations when retrieving data. This would be sufficient if a DBMS wasn't meant to work in a [[Distributed System]], for this very reason we need to also handle data races and conflicts. The job of handling access control is done by the **Transaction manager**, that as the name suggests, handles [[Transactions]].
### Reliability

An important aspect of a system is it's reliability -- the ability of something to perform a required function under stated condition. In databases this aspect is implemented through [[Replication]] and [[Logging]].
### Queries

Queries define a generic operation on data that is stored in a database and they are written in a dialect of [[SQL]].

[[Ranking queries]]
### ORM

