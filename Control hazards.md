---
tags:
  - computer_architecture
---
This is an attempt to make a decision on the next instruction to execute before the condition is evaluated. The problem is that we don't know what to execute after the branches before the program counter changes. So how can we prepare instructions in the pipeline? 
- We wait until we can know for sure what to execute by inserting `noop`s
- We make a [[Branch prediction]] and execute one branch, if the prediction happens to be wrong, then discard the previous computations and start with the new branch

>[!tip]
>We can use a EX/IF channel to anticipate from $3$ cycles to $2$ cycles or to include a ID/IF channel to go down to $1$ cycle
>
![[MIPS IDIF.png]]