---
tags:
  - databases
---
This is a virtual table defined with a query stored in the database catalog and then used in queries as if it were a normal table.

```mysql
create view <name> as
	select <...>
```
### Materialized view

Some systems support the `CREATE MATERIALIZED VIEW` command, which makes the view automatically materialized in the actual DBMS. This is done if some query frequently reuse the same view over and over. 

On systems that do no support this feature, we can emulate this behavior using [[Triggers]].