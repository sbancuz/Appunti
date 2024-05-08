---
tags:
  - computer_architecture
---
We are trying to solve the problem of having hazards due to true data dependencies that cannot be solved by forwarding cause of **stalls** of the [[CPU Pipelining]]. The solution to this problem is to allow **data independent instructions** behind to proceed. 

>[!note]
>This generates out of order commits and execution

