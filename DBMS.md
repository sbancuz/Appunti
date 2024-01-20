---
tags:
  - databases
---
The architecture of a database can be divided in two parts:
- The [[Physical database]] that handles how information is stored in the system
- The logical part that handles the retrieval of the information

![[query management.png]]

The **Query manager** handles the [[Query optimization]] step of execution that reduces the number of I/O operations when retrieving data. This would be sufficient if a DBMS wasn't meant to work in a [[Distributed System]], for this very reason we need to also handle data races and conflicts. The job of handling access control is done by the **Transaction manager**, that as the name suggests, handles [[Transactions]].
### Queries

[[Ranking queries]]
### SQL
TODO
#### View
This is a virtual table defined with a query stored in the database catalog and then used in queries as if it were a normal table.

```mysql
create view <name> as
	select <...>
```
#### Materialized view

Some systems support the `CREATE MATERIALIZED VIEW` command, which makes the view automatically materialized in the actual DBMS. This is done if some query frequently reuse the same view over and over. 

On systems that do no support this feature, we can emulate this behavior using [[Triggers]].
#### [[Triggers]]

Triggers can be used to define action upon meeting certain conditions.

```mySQL
create trigger <name>
{ before | after }
{ insert | delete | update [of <column>] } on <table>
	referencing {   [ old table [as] OT ]
					[ new table [as] NT ]
					[ old [row] [as] OldTuple ]
					[ new [row] [as] NewTuple ] }
[ for each { row | statement }]
[ when <condition> ]
<SQLProceduralStatement>
```
#### [[Indexes]]

These are structures used to speed up a database.

```mysql
create [unique | fullist | spatial] index name on
	tableName (attributeList) using { btree | hash }
```
### [[Transactions]]

In SQL we can change the isolation levels of [[Transactions]], this modifies which schedules are allow and which aren't

![[isolation level.png]]

To specify a transaction we use
```mysql
set [ local ] transaction 
```