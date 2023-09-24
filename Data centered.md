---
tags:
  - distributed_systems
---
The components communicate through a common repository, data can be added to this repository through [[RPC]] and the access is usually synchronized.

#### Linda

Data is contained in ordered sequences of typed fields (tuples) and stored in a persistent, global shared space. It has 3 standard operations :
- out(t) : writes a tuple t in the tuple space
- rd(p) : returns a copy of a tuple matching the pattern p, if it exists, otherwise it blocks waiting for a match
- in(p) : like rd but withdraws the matching tuple from the tuple space 

These are just the standard operations, but there can be many variations.
This does not scale well on WAN and the model is only proactive. And as a consequence, commercial applications provide only client access to a server holding the tuple space and introduce reactive procedures.