---
tags:
  - databases
---
[[Physical database]]

TODO
=
![[query management.png]]

### Queries
TODO

[[Query optimization]]

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
#### [[Physical database#Indexes]]

These are structures used to speed up a database.

```mysql
create [unique | fullist | spatial] index name on
	tableName (attributeList) using { btree | hash }
```

