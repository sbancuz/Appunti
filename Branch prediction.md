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
### Dynamic prediction

To use the past branch behavior to predict at runtime the future branch behavior. We need also to memorize the outcome of a branch inside some kind of hardware buffer, this buffer is put in the instruction fetch phase. We need to put 2 information in this buffer:
- Branch Outcome Predictor $\to$ it says to take or not to take
- Branch Target Buffer $\to$ holds the address of the branch in case the branch is taken

There are 4 techniques for dynamic branch prediction:
- Branch history table
	Table indexed by the lower portion k-bits of the address of the branch instruction, it will hold whether or not the branch was taken recently or not. The table **has no tags** so this prediction could be created by a different branch with the same low bits
 
- Correlating branch predictors
	The basic idea is to make prediction based on results of other branches, for example the behavior of 2 nested loops could be correlated. 

- Two-level adaptive branch predictors
	There is a global history table and a second level history table called **pattern history table** used locally

- Branch target buffer
	Is a cache storing the **predicted target address** for the taken branch instructions. This can be expressed as PC-relative