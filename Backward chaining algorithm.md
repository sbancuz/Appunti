---
tags:
  - artificial_intelligence
---
Backward chaining works backwards from a query. If $q$ happens to be true, then no work is needed, otherwise the algorithm finds those implication in the knowledge base whose conclusion is $q$. And if all the premises of one of those implication can be proven true, then $q$ is true. This runs in linear time.

Backward chaining is a form of **goal directed reasoning** and it's useful when answering specific questions and can be more efficient then other reasoning methods because it only touches the relevant information in the knowledge base.