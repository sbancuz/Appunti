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

Pipelining is a technique to increase throughput when scheduling operations, MIPS makes use of this execution schedule by using 4 register between the various phases of execution. This means that the time to execute for all the instructions is 5 cycles, but overall the speedup for the program is 5x at most. This can be measured with [[Performance metrics]].

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
- We make [[Branch prediction]] and execute one branch, if the prediction happens to be wrong, then discard the previous computations and start with the new branch

>[!tip]
>We can use a EX/IF channel to anticipate from $3$ cycles to $2$ cycles or to include a ID/IF channel to go down to $1$ cycle
>
![[MIPS IDIF.png]]
#### Dependence

All these problems fall under the same underlying region, **dependence**. If two instructions are dependent to each other, they cannot be executed in parallel, just in order or partially overlapped. There are 3 types of dependencies:
- True data dependencies / flow dependence
	An instruction $j$ is dependent on a data produces by $i$

- Name dependencies 
	Two instructions use the same memory location, these are the same as [[Parallelization#Data dependency]] when talking in general about parallelization. To resolve this problem, an easy fix would be to change the location where the data would be saved, like for example in another register. This specific action is called **register renaming**.

- Control dependencies
	A control dependence determines the ordering of the instructions and it's preserved by both the program order and the fact that an hazard cannot be allowed to happen before a branch direction is not known

### Multi cycle pipeline

Up until now we have considered **single issue** processors, i.e. one instruction per clock cycle. This is not ideal since requesting some memory or even some instructions may take more than one cycle to resolve, this means that the write back instruction will be delayed.  

To solve this issue we need to execute instruction out of order while the other, more latent instructions, are executing. But this now creates problems with anti and output dependence.

![[multi pipe.png]]

The key idea to solve all these hazards is **dynamic scheduling** and allow data independent instruction behind a stall to proceed -- all of this managed by the HW.

We can also define an exception to be **imprecise** when the processors state raises an exception, and the state produces is not the same as if the instruction where executed in-order. These type of exception are very hard to deal when they occur, because how would we know from what data to restart? So they have to be avoided like the plague.
#### Multiple issue pipeline

Since we dealt with all types of hazards, how can we still increase performance? Well just issue multiple instructions per clock and extend the processor architecture to deal with it -- just put more ways to read registers and some other ALUs.

In this case the dynamic scheduler will have to work overtime to resolve all dependencies and maximize throughput.
#### Very long instruction word

This is another type of architecture in contrast with dynamic scheduling. This takes advantage of static scheduling to deal with all the dependencies of the code to help scale performance better, in fact a pure dynamic scheduled approach has an upper bound of issues of 4. 
#### Scoreboard pipelining

We start by considering a **single-issue** processors where the IF are executed in-order, but the execution overall can be out-of-order -- this means that we also can have anti and output dependencies. Execution and memory stages can also take multiple cycles to finish.

>[!warning]
>We can't have forwarding and we can deal with imprecise interrupts

Scoreboard allows **data independent instructions behind a stall to proceed**. We can distinguish when an instruction begins execution and when it completes. 

![[scoreboard.png]]

The ID stage of an instruction can be divided in two stages:
- Issue $\to$ the decoding part that can check for structural hazards
- Read operands $\to$ Wait until all data hazards are resolved

To deal with anti-dependency we can read registers only during the Read Operands stage. To deal with Output dependency we can stall the new instruction until the previous one finishes.

![[scoreboard arch.png]]
### Tomasulo dynamic scheduler

