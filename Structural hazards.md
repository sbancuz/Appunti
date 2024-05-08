---
tags:
  - computer_architecture
---
It's an attempt by the CPU to use the same resource from different instructions simultaneously. To resolve this problem we can execute operations out of order, when no other hazards arise, or as a last case to perform `noop` instruction to delay the problematic computation. 

This process is done by the [[Compiler]]. In case the compiler does not do this step, the hardware can stop the execution of the hazardous operation, if it can detect one, by inserting an `stall` step to delay everything. This is the same as a `noop`. 

Another optimization is to utilize the values inside the interstage registers to perform computation before the write back step, this can solve reduce the execution time by some cycles. There are 2 types of data forwarding paths:
- EX/EX path
- MEM/EX path

![[MIPS paths.png]]