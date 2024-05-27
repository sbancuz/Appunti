---
tags:
  - computer_architecture
---
The basic idea of this architecture is to load **sets** of data elements into **vector registers**, then we can perform operations on them. This means that a single instruction operates on vectors, it has a single program counter. The main benefit of this type of architecture is that it leverages memory bandwidth.  

![[vector ops.png]]

In vector processors each result is **independent** of previous results. And, since they are mostly used whenever there is a lot of work -- i.e. in loops -- they can just leverage the instruction cache and prefetch data. 

There are also a couple of classes of vector architectures
- Memory-memory
- Vector-register

This type of architecture has many advantages:
- Very compact code
- Sometimes branches can be eliminated, for examples for very small vector computations
- Decrease in the amount of pipeline stalls, in fact the is only one for the first vector element

To increase the performance even more we need **operator chaining**. Since loading vectors isn't fast, we can just forward the result of one FU to another FU in the chain. This saves a lot of loading time. A bunch of this chain-able operations that can execute partially overlapped is called a **convoy**. 

>[!important]
>In [[MIPS]] the FUs consume **one element per clock cycle**, so the execution time is given approximately by the vector lenght.

A **chime** is a metric corresponding to a unit of time to execute one convoy. More simply for a vector length of $n$, and $m$ convoys in a program, $n \times m$ clock cycles are required.
### Multiple lanes

To improve performance even more, with the objective to have more than one operation per clock cycle, we can just use **multiple lanes** for the pipeline

![[SIMD multiple lanes.png]]

### Vector length control

The **Maximum Vector Length** is the physical length of vector registers in a machine. (64 in [[MIPS]])

But the problem is: how do you divide the work if the length of the program is not equal to the MVL?
- If it's known at compile time and it's smaller than the MVL we can use the vector length register
- If not, then we use **strip mining** to divide the elements in various segments

![[stripmining.png]]

If there also happen to be a control dependence in the loop we can use the **vector mask register** to disable some elements. When this registers are enable operations are only allowed on the vector elements whose corresponding masks bits are set to $1$.