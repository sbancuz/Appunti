---
tags:
  - computer_architecture
---
This is an extension of the idea of [[Dynamic scheduling]].  In fact it encompasses 3 key concepts:
- Dynamic branch prediction
- Speculation to enable execution before control dependencies are resolved
- Dynamic scheduling in general

The idea is to enable the execution of instructions **before** the control dependencies are solved and save the intermediate results in a buffer called the **ReOrder Buffer**. This enables out-of-order execution but in-order commit. Another application of these ROB is to use them as a reservation stations -- like for [[Dynamic scheduling#Tomasulo dynamic scheduler]].

![[speculative tomasulo.png]]

To keep this order each entry needs to keep track of both **the status of an instruction** and if said instruction is in **speculative execution**. An instruction can only commit iff:
- It has finished
- Not marked as speculative
- All previous instructions have already retired

More formally each entry in the ROB contains
	| Busy field | Instruction type field | Destination field | Value | Ready field | Speculative field |
and are stored inside a circular buffer. 
### Speculative [[Dynamic scheduling#Tomasulo dynamic scheduler]]

The main difference is that pointers are directed to the **ROB** entries instead of the reservation stations and there is one more phase of execution. So they are
1) Issue
	If there are any RS entries free and one ROB entry free then we can issue an instruction. If its operands are available in a RF or in ROB, they are sent to RS. If RS or/and ROB is full then just stall.

2) Execution start
	When both operands are ready in the RS start to execute. If they are not just monitor the CDB for the results. 

3) Execution completed
	Write the result present on the CDB to awaiting FUs **AND** to the ROB value field. Mark the RS as available 

4) Commit
	When instruction at the head of ROB and the result is ready, update RF with the result and remove the instruction from the ROB. There are 3 possible commit phases
	- Normal commit 
		if the instruction is at head of ROB and result in buffer the store result in the register file
	
	- Store commit
		as above, but the result is stored in memory rather then in the RF
	
	- Mispredicted branch 
		the speculation was wrong, so flush the ROB and restart the execution from the correct successor of the branch
