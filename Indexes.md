---
tags:
  - databases
---
Data structure that help efficiently retrieve tuples on the basis of a **search key**. They are composed as
$$
[\text{Search key, pointer to block}]
$$
We have two types of indexes depending on their density:
- dense $\to$ an index for each search-key value in the file
- sparse $\to$ only for some search-key value, this can only be used in ordered table

We can also define:
- primary indexes $\to$ 
	the search key is **unique** and coincides with the attribute according to which the structure is ordered
- secondary index $\to$ dense index with an order different from the sequential order of the file
- clustering index $\to$ generalization of the primary but with **non unique** keys

>[!warning]
>These terms are not universal between documentations/systems
#### Guidelines
1) Do not index small tables
2) Index primary key of a table if it's not a key of the primary file
3) Add secondary index to any column that is heavily used as a secondary key
4) Add a secondary index to a Foreign Key if it's frequently accessed
5) Add secondary  indexes on columns that are involved in selection, join, order by, group by, union or distinct
6) Don't index frequently modified table
7) Don't index a column if a query will retrieve most of the records in the table
8) Don't index long strings

