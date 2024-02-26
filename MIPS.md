---
tags:
  - computer_architecture
---
The MIPS architecture is a type of open CPU that has 32 general purpose registers organized in a **Register File** with 2 reads port and 1 write port. MIPS is also considered a predecessor of the RISC architecture.

![[MIPS arch.png]]

### Instruction format

Register $R$, immediate $I$, jumps $J$.

![[instr format mips.png]]
### Instruction set

```asm
# Arithmetic operations
add  $s1, $s2, $s3              # $s1 $\gets$ $s2 + $s3
addi $s1, $s2, IMM              # $s1 $\gets$ $s2 + IMM

# Memory opeartions
lw   $s1, offset ($s2)          # $s2 $\gets$ M[$s2+offset]
sw   $s1, offset ($s2)          # M[$s2+offset] $\gets$ $s1

# Branch instructions
eq   $s1, $s2, L1               # go to L1 if ($s1 == $s2)
bne  $s1, $s2, L1               # go to L1 if ($s1 != $s2)
j    L1                         # go to L1
jr   $s1                        # go to add. contained in $s1
```

>[!note]
>These are not all the instructions, but are enough to understand the course
### Phases of execution

1) Instruction fetch $IF$
	Send the content of **Program Counter** register to **Instruction Memory** and fetch the current instruction from Instruction Memory
2) Instruction decode and register read $ID$
	Decode the current instruction (fixed-field decoding) and read from the **Register File** of one or two registers 
3) Execution $EX$
	The ALU operates on the operands prepared in the previous cycle depending on the instruction type
4) Memory access $ME$
	Access the memory needed either for writing or reading. In case of a branch change the Program Counter
5) Write back $WB$
	Write the data of the result to the destination register
### Pipelining

Pipelining is a technique to increase throughput when scheduling operations, MIPS makes use of this execution schedule by using 4 register between the various phases of execution. This means that the time to execute for all the instructions is 5 cycles, but overall the speedup for the program is 5x at most.

![[pipelining.png]]

One important detail is that to perform pipelining we need to add **pipeline registers** to hold the intermediate values of the computation.

The problems with pipelining are **data dependency** and **jump instructions**, and we can categorize these hazards in 3 classes:
#### Structural hazards

This is an attempt to use the same resource from different instructions simultaneously. To resolve this problem we can execute operations out of order, when no other hazards arise, or as a last case to perform `noop` instruction to delay the problematic computation. This process is done by the [[Compiler]]. In case the compiler does not do this step, the hardware can stop the execution of the hazardous operation, if it can detect one, by inserting an `stall` step to delay everything. This is the same as a `noop`. Another optimization is to utilize the values inside the interstage registers to perform computation before the write back step, this can solve reduce the execution time by some cycles. There are 2 types of data forwarding paths:
- EX/EX path
- MEM/EX path

![[MIPS paths.png]]
#### Data hazards

This is an attempt to use the result before it's ready, this is for the Load/Store operations. To resolve these we can add another path:
- MEM/MEM path
#### Control hazards

This is an attempt to make a decision on the next instruction to execute before the condition is evaluated. The problem is that we don't know what to execute after the branches before the program counter changes. So how can we prepare instructions in the pipeline? 
-  We wait until we can know for sure what to execute by inserting `noop`s
- We make **predictions** and execute one branch, if the prediction happens to be wrong, then discard the previous computations and start with the new branch

>[!tip]
>We can use a EX/IF channel to anticipate from $3$ cycles to $2$ cycles or to include a ID/IF channel to go down to $1$ cycle
>
![[MIPS IDIF.png]]
### Performance metrics

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
