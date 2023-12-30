---
tags:
  - artificial_intelligence
---
The forward chaining algorithm determines if a single proposition symbol is entailed by a knowledge base of definite clauses. It begins from a known fact in the knowledge base, if all the premises of an implication are known, then its conclusion is added to the set of known facts. This process continues until the query is added to the knowledge base of no more inferences can be made. This runs in linear time.

This algorithm is an example of **data driven** reasoning -- that is, reasoning in which the focus of attention stats with the known data.