---
tags:
  - computer_architecture
---
Pipelining increases the CPU instruction **throughput**, but it does not reduce the execution time of a single instruction. In fact, pipelining usually slightly increases the latency of each instruction due to the imbalance among the pipeline stages and overhead in the control of the pipeline:
- Imbalance among pipeline stages reduces performance because the clock can run no faster than the time needed for the slowest pipe stage.
- Pipeline overhead arises from the delay introduced by interstage registers and clock skew.
- All instructions should be the same number of pipeline stages.

To start off we need to define the unit of time for which we need to evaluate the performance
$$
T_{clk} \qquad \text{or} \qquad f_{clk}
$$
Using this we can define the **execution time** or **CPU time** as
$$
\text{CPU time} = \text{Clocks } \times T_{clk} = \frac{\text{Clocks}}{f_{clk}}
$$
This however does not tell us much about how the hardware is actually performing, to have a more fine grained view we need to use the **instruction count** $IC$ and relating it to the time with the $CPI$ or **clocks per instruction** to better measure performance
$$
\text{CPU time} = \frac{secs}{program} = IC \times CPI \times T_{clk}
$$
And of course, we have that the **instructions per clock** are 
$$
\text{IPC} = \frac{1}{CPI}
$$
However it may not be the case that all instructions take the same length of time, so we need to divide
$$
\text{CPI} = \sum (CPI_{i} \times \underbrace{ f_{i} }_{ instruction frequency })
$$
>[!note]
>For a lot of metrics is more manageable to work with **Million Instructions Per Second** 
>$$
> \text{MIPS} = \frac{IC \times CPI}{f_{clk}}
$$
### Amdahl's law

We can define the speedup due to an enhancement $E$ as 
$$
\text{Speedup}(E) = \frac{\text{ExTime w/o }E}{\text{ExTime w/ }E} = \frac{\text{Perf w/ }E}{\text{Perf w/o }E}
$$
>[!note]
>See also [[Time complexity for PRAM#Amdahl's law]] for evaluating performance in parallel applications

The basic idea derived from this law is to **make the common case fast**.
$$
SU(P,f) = \frac{T_{1}}{T_{P}} = \frac{1}{(1-f)+\frac{f}{P}}, \lim_{ P \to \infty } {SU(P,f)=\frac{1}{1-f}}
$$
Where $P$ is the speedup gained from parallelism only for the parallelizable task.
### Performance for [[CPU Pipelining]]

Pipelining increases the CPU **throughput**, but does not reduce **latency** of single instructions. The first important difference that comes to mind is about the clock cycles needed to execute a task
$$
\text{Clocks } = IC + \text{Stalls} + 4 \text{ (for the 5-stage pipeline to finish)}
$$
Thus impacting all other metrics. Where it doesn't effect is the asymptotic evaluation of a program since $4$ clock cycles in the grand scheme of things is negligible, the real difference is in the stalls.

The **ideal** CPI on a pipelined processor would be $1$, but this is never the case due to stalls. Because of this we can introduce the
$$
CPI_{avg} = CPI_{ideal} + \text{Stalls}
$$
### Memory hierarchy

A big part that we just ignored up until now are the memory accesses. This take a very long time, with respect to other instructions, and can even take variable time depending if they are in a [[cache]] memory or not. We can define the **hit rate** and **miss rate**
$$
\text{Hit rate} = \frac{\text{Hits}}{\text{Mem accesses}} \qquad \text{Miss rate} = 1 - \text{Hit rate}
$$
A [[cache]] miss however results in a penalty in performance
$$
\text{Miss time }= \text{Hit time} + \text{Miss penalty}
$$
and typically we have that $\text{Hit time} << \text{Miss penalty}$. In general we can define the **average memory access time** as
$$
AMAT = \text{Hit rate} \times \text{Hit time } + \text{Miss rate } \times \text{Miss time} = \text{Hit time} + \text{Miss rate} \times \text{Miss penalty}
$$
Since there are multiple levels of [[cache]] this average time is for a single layer of memory. To evaluate a more general notion of miss rate we use the **global miss rate** -- that is, when the CPU fetches data directly from the ram.
$$
\text{Global miss rate} = \prod \text{Miss rate}_{Li}
$$
### Multiprocessors

We define $P$ the number of nodes, $M$ the number of links and $b$ the bandwidth of a single link. The **Total Network Bandwidth** is 
$$
\text{TNB }= M \times b
$$
We also define the **Bisection Bandwidth**, this is the division of the machine into two parts, each with half the nodes, then you sum up the bandwidth of the links that cross that imaginary dividing line.

>[!note]
>Some networks are not symmetric -- see [[Multi-processors]]. To find the worst case metric we need to choose the division that yields the most pessimistic network performance