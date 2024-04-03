---
tags:
  - computer_architecture
---
Register renaming is a technique to avoid WAR and WAW [[MIPS#Data hazards]] that is executed, in most cases, in the compilation step. The basic idea is to use different register to compute the same result. 
### Loop unrolling

This is a simple compiler transformation that writes all the operations of a given loop sequentially. This helps with both branch prediction, since there are no more branches, and with RAW hazards that are present between the iterations.

>[!note]
>There can also be partial loop unrolling, this is constrained by [[SIMD#Loop carried dependencies]] and/or multiples of the *iteration_count*


