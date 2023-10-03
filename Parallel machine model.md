---
tags:
  - parallel_computing
---
### RAM (Random access machine)

It'a a theoretical machine that is:
- unbounded number of local memory cells
- each memory can hold an integer of unbounded size
- instruction set includes simple operations
- all operations take unit time

The time complexity represent the number of instruction executed and the space complexity are the number of cells used.

### PRAM (Parallel RAM)

It's an abstract machine for designing the algorithms applicable to parallel computers. It's represented as a system of infinitely many rams. Prams are useful because can describe in a very natural and simple way and can be used to benchmark applications. 
It's characterized by :
- unbounded collection of RAM processors
- unbounded collection of share memory cells
- all processors can access all the memory cells in unit time
- all communication is done through shared memory

There are 5 steps in pram computation:
- read all values form the input $x_{1},\dots x_{n}$
- read one of the shared memory cell $a_{1},a_{2},\dots$
- performs the shared computation
- may write into one of the output cell $y_{1},y_{2},\dots$
- may write into one the shared memory cell $a_{1},a_{2},\dots$

During the computation can remain idle, this could happen when in the algorithm there is a branch.

Prams are classified based on their read/write abilities:
- ER : Exclusive Read -> Read from distinct memory location
- EW : Exclusive Write -> Write from distinct memory location
- CR : Concurrent Read -> Read from the same memory location
- CW : Concurrent Write -> Write from the same memory location

To deal with CW we could implement some kind of priority on the processor.
### [[Time complexity for PRAM]]
### Variants of PRAM

1) Bounded number of shared memory cells
#### Lemma

Any problem that can be solved for a processor $P$ and $M$ cells in $T$ steps can be solved on a $\max(P,M')$ processors $M'$ cell pram in $O\left( \frac{TM}{M'} \right)$

2) Bounded number of processor
#### Lemma

Any problem that can be solved for a $P$ processor pram in $T$ steps can be solved in a $P'$ simulating processor pram in $T'=O(\frac{TP}{P'})$ steps, assuming shared memory.

3) Bounded size of a machine word
4) Handling access conflicts
