---
tags:
  - computer_architecture
---
The MIPS architecture is a type of open CPU that has 32 general purpose registers organized in a **Register File** with 2 reads port and 1 write port. MIPS is also considered a predecessor of the RISC architecture.

MIPS is also an architecture that, like every other architecture, relies heavily on [[CPU Pipelining]].

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

The idea is that this scheduler does is [[Register renaming]] to remove any WAW and WAR  hazards. This is achieved by using some buffers called **reservation stations** in front of the function units to hold pending operations before executing them. Tomasulo kind of works like a scoreboard, but the main difference is that we don't have a centralized buffer that will hold all pending operations, but a distributed one. The result of a computation is broadcasted to all the functional units and to all store buffers.

![[tomasulo.png]] 

There are 3 stages of the Tomasulo pipeline
1) Issue 
	Get an instruction from the instruction queue, check for structural hazards in the reserving stations (**RS**) in if needed add some stalls. If the operands are not yet ready in the register file (**RF**) then we need to keep track of the FU that will produce them. This is the step of renaming.

2) Start execution
	Once both the operands and the functional units are ready we can start the execution, if they aren't, just monitor the shared bus for the results that we need. The loads and stores works a little bit differently, first they compute the effective address then they will try to execute. To preserve exception behavior no instruction can be executed until all branches before are resolved, if branch prediction is used, then the CPU must know the prediction correctness.

>[!Important]
> The load/store operation are kept in order

3) Write result
	Broadcast the result of the operations to the shared buffer and, if needed, write the result to the memory.