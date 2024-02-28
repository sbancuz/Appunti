---
tags:
  - computer_architecture
---
Pipelining increases the CPU instruction throughput, but it does not reduce the execution time of a single instruction. In fact, pipelining usually slightly increases the latency of each instruction due to the imbalance among the pipeline stages and overhead in the control of the pipeline:
- Imbalance among pipeline stages reduces performance because the clock can run no faster than the time needed for the slowest pipe stage.
- Pipeline overhead arises from the delay introduced by interstage registers and clock skew.
- All instructions should be the same number of pipeline stages.

To evaluate the performance of the execution we define:
- $IC$ $\to$ Instruction count
- $CPI = \text{Clock cycles} / IC$ $\to$ Clocks per instruction 
- $IPC = 1 / CPI$$\to$ Instruction per clock 
- $\text{Clock cycles} = IC + \text{Stall cycles} + 4$
- $MIPS = f_{clock} / (CPI * 10^{6})$ $\to$ Million instruction per second

