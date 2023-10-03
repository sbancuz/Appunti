---
tags:
  - parallel_computing
---
| Symbol | Definition |
| --- | --- |
| $T^{*}(n)$ | Time to solve problem on one processor |
| $T_{p}(n)$ | Time to solve on $p$ processors |
| $SU_{p}(n) = \frac{T^{*}}{T_{p}}(n)$ | Speedup on $p$ processors |
| $E_{p}(n) = \frac{T^{*}}{pT_{p}}(n)$$ | Efficiency |
| $T_{\infty}(n)$ | Shortest run time on any $p$ |
| $C(n) = P(n)T(n)$ | Cost of processors and time |
| $W(n)$ | Work = total number of operations |

>[!example]
>![[Logarithmic sum]]

### Amdahl's law

He was one of the three architects of IBM mainframes in 1967 and he objected to parallelism. In his model a computation can be divided in 2 segments:
- sequential 
- parallelizable

And so a computation can be divided in either a sequential work done by a singular processor or some batches of work done by others.
