---
tags:
  - databases
---
A DBMS doesn't just execute the query, it performs several steps to optimize the query before executing it.

![[query optimizer.png]]

This optimization step is divided in:
- Lexical, syntactic and semantic analysis
- Translation into an internal representation similar to algebraic trees
- Algebraic optimization
- Cost based optimization
- Code generation
### Relation profiles

Profiles are stored in the **data dictionary** and contain quantitative information about tables:
- cardinality $\to$ number of tuples 
- dimension in bytes of each attribute
- number of distinct values of each attribute $T: Val(A_{j})$
- min and max val for each attribute

These profiles are used in cost based optimization for estimating the size of the intermediate results produced by the query execution plan. We can define the **selectivity** as the probability that any row will satisfy a predicate.

$$
Val(A) = N \implies P(A = k) = \frac{1}{N} \text{ assuming even distribution} 
$$

>[!warning]
>If no information is available we assume an even distribution

![[03_Physical_Databases_Schema.pdf#height=2322]]