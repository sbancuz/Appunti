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
![[amdahl.png]]
This means that
$$
SU(P,f) = \frac{T_{1}}{T_{P}} = \frac{1}{(1-f)+\frac{f}{P}}, \lim_{ P \to \infty } {SU(P,f)=\frac{1}{1-f}}
$$
![[amdal.png]]

### Gustafson law

In 1988 Gustafson didn't agree, because he managed to achieve a speedup that is linear to the number of processors at a large scale. In this case we disregard the idea of having a fixed portion of the workload. This law shows that the computing resources can be scaled up to utilize the available resources effectively.
$$
SU(P) = s + P(1-s)
$$
where $s$ is the fixed time to compute the serial part.