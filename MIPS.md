---
tags:
  - computer_architecture
---
The MIPS architecture is a type of open CPU that has 32 general purpose registers organized in a **Register File** with 2 reads port and 1 write port. MIPS is also considered a predecessor of the RISC architecture.

MIPS is also an architecture that, like every other architecture, relies heavily on [[CPU Pipelining]] and [[Hardware based speculation]]

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


