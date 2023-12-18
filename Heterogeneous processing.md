---
tags:
  - parallel_computing
---
Most real world applications have complex workload characteristics, they may
- [[Parallelization|Parallelizalible]] or not
- Have SIMD patterns
- Be predictable or not

To handle such a complex and diverse system the best solution is to make everything heterogeneous. This means that a system can provide system that can optimize and perform workloads faster because they are specialized to do only that one thing. 

An advantage of this approach is to also be able to reduce the power consumption of the system.
$$
\text{Power} = \frac{\text{Op}}{\text{second}} \times \frac{\text{joules}}{\text{Op}}
$$
The idea now is to reduce the total energy consumption of every operation. There are 2 main techniques to achieve that:
- Use specialized processors
- Move less data

Specialized processors are way more efficient than their counterpart because general purpose processors have to do a lot of work just to do a simple arithmetic operation -- decoding the op, loading the data into specific registers, computing the result and writing it to some other part of the memory --, on the other hand if we were to just do the actual computation that would be much faster. Examples of this dedicated hardware are GPUs, FPGAs or ASIC processors.

![[heterogeneous pro.png]]

The problem with this approach is that is not always applicable everywhere, heterogeneous systems are by design harder to realize, use and maintain.
### Heterogeneous parallel programming

The ideal programming language provides: productivity, performance and generality.

![[DSL.png]]

The 3 principles are really hard to achieve at the same time. And because of this there exists domain specific languages that can interop with general purpose programming languages to speed them up in certain tasks. However this approach can be tedious because it requires **manually** building a program and data structures to exploit these languages. One such example of DSL is [[Halide]] 