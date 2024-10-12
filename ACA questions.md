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