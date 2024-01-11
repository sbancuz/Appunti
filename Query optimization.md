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
