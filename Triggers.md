---
tags:
  - databases
---
Triggers is a rule that allows to automatically execute an action on a database, these actions can be triggered by insert, update and delete [[SQL]] operations.

They can be used to specify complex behavior and constraints on data. A trigger consists of:
- Event
- Condition
- Action

>[!note]
>They are compiled and stored in the DBMS like [[Stored procedures]].
### Syntax

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
### Execution modes

Execution modes define when a trigger gets checked to the database and they vary depending on the time.
There are 2 execution modes:
- Before $\to$ The action is triggered **before** the database status changes, used as a validation constraints
- After $\to$ The action is triggered **after** the database modification of the database
### Transition table

We can also specify where the action gets applied with the `for each` keywords. They specify if a rule has to be checked with a different level of granularity. There are 2 types:
- Row-level $\to$ The trigger is considered once **for each tuple** affected by the statement
- Statement-level $\to$ The trigger is considered once **for each activating** statement

These transformations holds 2 types of data: **new** and **old** depending on the granularity level. This information is stored in the transition table of the trigger.