---
tags:
  - compilers
---
This is a [[Non-deterministic finite state automaton]] but with auxiliary memory structured as an unbounded stack of symbols where only 3 operations are allowed:
- push
- pop
- check for emptiness

A move consists of reading the current character and shifts the input head, then pop the stack if it's not empty and depending on the current character it goes into the next state and may places something on the stack.  

![[PDAUTOMATA states.png]]

![[PDFSM exa.png]]

