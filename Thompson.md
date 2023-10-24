---
tags:
  - compilers
---
 It's an algorithm that decompose the regex in subexpressions until we have atomic constituents, then construct various subexpression recognizer and connect them. 
 
![[regex to fsm.png]]

In general, the outcome of the Thompson method is anon-deterministic automaton with spontaneous moves.