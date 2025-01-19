---
tags:
  - computer_architecture
---
## Static instruction scheduling

> Explain the main concepts of the technique

Static instruction scheduling is the concept of trying to optimize, schedule and resolve conflicts for the execution of a program at compile time. The idea is to try to exploit ILP by detecting whether some instruction can be re-ordered to speed up the execution, in the case of a multiple issue processors, like for VLIW machines, this can come also in the form of trying to parallelize some instructions. Since the compiler can't know anything about the run-time context of the execution, it uses register renaming to resolve WAR and WAW conflicts since they do not come from true data dependencies. NOPs can also be inserted to resolve conflicts in case we can't insert any other instruction. To create this schedule the compiler divides the program in basic blocks, that means chunks of code that don't contain any branch instructions, and, by creating a dependence graph, they can schedule the execution using the list based scheduling algorithm. There are also some static code transformation that can cross basic blocks, these are loop unrolling and software pipelining.

> Main benefits

Static instruction scheduling is good for small chips for embedded devices, this is because they are simpler to make, in the sense that you just need a good compiler that can optimize well for the desired architecture, and are a lot cheaper since it doesn't need a lot of hardware to deal with hazards and are overall simpler. Good compiler support also gives them very good performance since the compiler can optimize the code looking at a wider instruction window, not just basics blocks.

> Main drawbacks

The main drawback of static instruction scheduling is the low code portability. Since each compilation heavily relies on the target architecture to make certain optimization, like "how many FPUs do we have?", each binary is tailored to a specific CPU, not even the whole ISA. So the compiled binary will perform a lot worse, or not even function, if those assumptions are broken. There is also a huge number of register renaming involved, so the register file has to be more complex. Good compiler support can also be a drawback since it's not always present, and it's not something that is easy to develop, especially if the architecture keeps changing. Static scheduling can't deal with some run-time exceptions like branch misses and cache misses, so there is still a small need for some dynamic behavior involved.

> Hardware resources

Static scheduling, although needs a smaller die overall since most of the scheduling logic is moved to the compiler, it still needs a lot of functional units to be able to parallelize the execution, and a good enough register file to be able to issue instruction faster, or even in parallel. In the case where we have more functional units for each type than the number of issues, we can also use a dispatch network to pick dynamically which functional unit will execute the instruction.

### Dynamic scheduling

> Explain the main concepts of the technique

Dynamic scheduling tries to maximize the performance of a processor at run-time. All conflicts have to be resolved during the execution of the program by means of stalling or implicit register renaming. The former means to halt the execution of an instruction if some dependencies can't be resolved and something else can't be rescheduled whilst they do. While the latter is the process of resolving WAR and WAW by using reservation stations that can hold the pending operands while they wait to be used by their functional unit. This generates out-of-order execution and commit. Dynamic scheduling can also allow for speculative execution. 

> Main benefits

Dynamic scheduling always brings very high performance. It leads to very portable code since all the CPU specific optimization can be done by the hardware and can deal with an imprecise exception model.

### Static branch prediction

> Explain the main concepts

Static branch prediction is a technique used to improve performance to control hazards, by removing the 1-cycle stall if we consider a fully pipelined MIPS CPU with early evaluation of the program counter in the ID stage, using compile time hints or by defining hard branch prediction behavior at compile time. To achieve this improvement in performance we can use: Branch always taken, Branch always not take, Backward taken forward not taken, profile driven prediction and lastly delayed branch. Some of these techniques, like for instance the branch always taken, require to add a hardware buffer called the Branch Target Buffer to hold the result of the address resolution and to start fetching the data.

> Main benefits

There is little to no HW required to implement such techniques, in it's the compiler's job to optimize and choose the correct branch behavior. So it cuts down on the die size, the cost and improves the power usage.

> Main drawbacks

Like other compile time techniques, it's far slower than a dynamic one. The main problem is that we have no information about the runtime behavior of the program so a branch could very well mispredict 100% of the times if the compiler does a bad enough job. It also needs some way to correct mispredictions by flushing instructions. 

> How does delay branch work?

Delayed branch works by trying to take advantage of the fact that there is at least a cycle in which it knows that it has to stall the execution. So the idea is to try to schedule something during that cycle by using static scheduling. This instruction can come from 4 different places: from before, from after, from taken and from fall through. If we can manage to reorder an instruction from before or from after we would want a branch independent instruction so that it would never be flushed. In the last 2 cases the instruction can be flushed in case of a misprediction
### Dynamic branch prediction

> Main concepts

Dynamic branch prediction has the job to minimize the impact of control hazards by exploiting runtime behavior. Dynamic branch prediction relays on 2 hardware components: BTB that is used to store the effective address of the prediction in case of branch taken, and the BOP that says which type of prediction is being performed.  There are various schemes for dynamic branch prediction: 
- Branch history table $\to$ we have a table indexed by the low part of an address that works as a state machine that saves the history of the branches and infers upcoming branch behavior
- Correlating branch predictors $\to$ we try to correlate the branch behavior of possibly related branches using branch history tables
- Two-level adapting branch predictors $\to$ it exploits more of the global branch behavior to correlate and make predictions, it uses a branch history buffer to hold the branch behavior history and it uses it, possibly adding local information about the branch, to index a table of n-bit branch predictors
- Branch target Buffer $\to$ we use a direct mapped cache to store the target address for the taken branch instruction, it also uses the tag to do the associative lookup. This can also be used to hold a 1/2-bit branch predictor in the same line of cache

> Main benefits

This technique is very fast and uses all the available information to make the most accurate predictions, thus minimizing the cost of branches.

> Main drawbacks

Very hard and costly to implement. It requires multiple hardware components to hold all available runtime information and to correct mispredictions.

> Correlating branch predictors

The idea is to expand the n-bit branch predictor to hold global history information. The idea is to use the last m predictions to choose which of the 2^m branch history tables to index to get the n-bit branch predictor. In fact the n-bit branch predictor is a special case of correlating branch predictor without global history i.e. (0, n)-correlating branch predictor.
### Reorder buffer

> Main purpose in the Tomasulo

The main purpose of the Reorder buffer is to enable speculative execution and port the Tomasulo architecture from an out-of-order commit one to an in-order one. This also improves upon the exception behavior because it becomes a precise one. This is achieved by a circular buffer, that is the Reorder buffer, that holds the results of the instructions until they can be committed to memory/registers in program order. So we have that the write back stage is divided in 2 stages: execution complete and write back.

> How does it support speculative execution?

By holding onto the results of executed, but not yet committed, instruction we can allow speculative execution without affecting any memory location. So we can delay to flush or commit an instruction until we know for certain the branch behavior. 

> Fields of the ROB

- Busy field $\to$ if the ROB entry is busy or not
- Instruction type $\to$ which type of instruction (ALU, Load/Store, FP operation)
- Destination $\to$ where to store the value once it gets committed, this can be a register or a memory location
- Value $\to$ the result of the instruction to hold on to
- Ready $\to$ if the instruction is ready to be committed
- Speculative $\to$ if it's being executed speculatively or not.

> 4 Stages of the Speculative Tomasulo

1) Issue $\to$ If we have a free ROB entry and RS we can issue the instruction and populate the hardware buffers. If not stall
2) Execution start $\to$ If there aren't any RAW, begin execution. If not monitor CDB until it can be executed
3) Execution complete $\to$ Write back the result in the value field of the ROB and clear the FUs and RS
4) Write back $\to$ If the instruction is on the head of the ROB, then if it's not speculative just commit to memory/RF and advance the head pointer. If it's speculative this instruction must come from a mispredicted branch so we can just flush it. In the case we are committing a branch instruction we need to clear all the speculative bits from the relevant instructions