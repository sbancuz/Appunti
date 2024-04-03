---
tags:
  - computer_architecture
---
This is an extension of the idea of [[Dynamic scheduling]].  In fact it encompasses 3 key concepts:
- Dynamic branch prediction
- Speculation to enable execution before control dependencies are resolved
- Dynamic scheduling in general

The idea is to enable the execution of instructions **before** the control dependencies are solved and save the intermediate results in a buffer called the **ReOrder Buffer**. This enables out-of-order execution but in-order commit. Another application of these ROB is to use them as a reservation stations -- like for [[MIPS#Tomasulo dynamic scheduler]].

![[speculative tomasulo.png]]

To keep this order each entry needs to keep track of both **the status of an instruction** and if said instruction is in **speculative execution**. An instruction can only commit iff:
- It has finished
- Not marked as speculative
- All previous instructions have already retired

More formally each entry in the ROB contains
	| Busy field | Instruction type field | Destination field | Value | Ready field | Speculative field |
and are stored inside a circular buffer. 