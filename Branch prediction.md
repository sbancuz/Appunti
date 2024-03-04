---
tags:
  - computer_architecture
---
It's a method for solving a [[MIPS#Data hazards]] that assumes a given outcome for the branch and proceeds speculatively from that assumption rather than waiting to certify the actual branch outcome. There are 2 types of branch prediction techniques:
- Static prediction, so done at compiler time
- Dynamic prediction, so done at runtime
### Static prediction

The actions for a branch prediction are fixed at compile time for each branch during the entire execution. This type of technique is **highly predictable**.

>[!note]
>From now on we will consider the [[MIPS]] architecture that jumps in the ID phase

There are 5 different techniques to achieve this:
- Branch always not taken
- Branch always taken
- Backward branch taken forward not taken
- Profile driven prediction
- Delayed branch

