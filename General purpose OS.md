---
tags:
  - OS
---
General purpose [[Operating System|OS]] weigh more **fairness and throughput** to give the smoothest experience possible. They have a notion of CPU time slices, preemption and priority, but they are organized in the **best effort way**. This means that there are not guarantees for deadlines.

High priority tasks usually get preference over low priority ones, however they still get to consume their share of CPU time

![[GPOS shcedule.png]]

General‐purpose systems are designed to handle diverse workloads efficiently, but there’s an inherent
trade‐off. The fairness and preemption mechanisms ensure that resources are shared, but deadlines
might sometimes be missed.

