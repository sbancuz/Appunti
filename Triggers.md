---
tags:
  - databases
---
Triggers is a rule that allows to automatically execute an action on a database, these actions can be triggered by insert, update and delete [[SQL]] operations.

>[!warning]
>All operations are a part of a **standard** not **implementation**, this means that some details may vary from system to system.

They can be used to specify complex behavior and constraints on data. A trigger consists of:
- Event
- Condition
- Action

>[!note]
>They are compiled and stored in the DBMS like [[Stored procedures]].

### Execution modes

Execution modes define when a trigger gets checked to the database and they vary depending on the time.
There are 2 execution modes:
- Before $\to$ The action is triggered **before** the database status changes, used as a validation constraints
- After $\to$ The action is triggered **after** the database modification of the database

In the standard there are no specification on what trigger has priority to execute before another, the only thing that matters is the execution mode, thus if there are several triggers in the same category, the order of execution depends of the system implementation.

![[standard udpate prio.png]]

>[!warning]
>A trigger action may cause another trigger to fire, this may lead to recursive calling of triggers. Thus emphasis is put on ensuring that a trigger can terminate.
### Transition table

We can also specify where the action gets applied with the `for each` keywords. They specify if a rule has to be checked with a different level of granularity. There are 2 types:
- Row-level $\to$ The trigger is considered once **for each tuple** affected by the statement
- Statement-level $\to$ The trigger is considered once **for each activating** statement

If the operation is an update then these transformations holds 2 types of data: **new** and **old** depending on the granularity level. This information is stored in the transition table of the trigger.
### Termination analysis

It's important to ensure that recursive cascading does not produce undesired effects and that this process will eventually terminate. The simplest type of checking exploits the **triggering graph**, this is a [[Graphs]] with
- A node $i$ for each trigger $T$
- An arc from a node $i$ to a node $j$ if the execution of $T_{i}$ may activate $T_{j}$ 

If this graph is acyclic, then we are sure that it will terminate, if not it may terminate or not. 
### Applications

There are 3 main applications for triggers:
- Data replication
- Integrity constraints
- [[DBMS#Materialized view]] maintenance