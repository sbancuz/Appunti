---
tags:
  - parallel_computing
---
An amortized analysis is any strategy for analyzing a sequence of operations to show that the average cost per operation is small, even though a single operation within the sequence might be expensive. The probability is not involved in this calculation.

>[!example]
>
How can we know how large a given data structure should be? We have to allocate enough memory for the program to not overflow, but minimizing its size. This is done using [[Dynamic tables]].

There are three common amortization arguments:
- aggregate method 
- accounting method
- potential method

No method is **best**, and in the case of accounting and potential method different schemes may yield radically different bounds.

The [[Dynamic tables]] example is a case of the aggregate method and is, though simple, lacking in any kind of precision in respect to the other methods.
RIVEDERE LEZIONE PERCHE NON C HO CAPITO NULLA DELLE ACCOUNTING
==


The idea of the potential method is very similar to the accounting method but the framework is:
- Initial data is $D_{0}$
- Operation $i$ transforms $D_{i-1}$ to $D_{i}$ with cost $c_{i}$
- Define a potential function $\Phi:\{ D_{i} \} \to R$ such that $\Phi(D_{0}) = 0$ and $\Phi(D_{i}) \geq 0$
- The amortized cost is $\dot{c_{i}} = c_{i} + \Phi D(i) - \Phi(D_{i-1})$

If $\Delta\Phi_{i}> 0$ then we are storing work for later use and $\dot{c_{i}}>c_{i}$, the contrary otherwise.
We also define the potential of the table after the $i$ insertion by $\Phi(D_{i})=2i-2^{\lceil \ln i\rceil}$ and it's average cost is
$$
\dot{c_i} = \begin{cases}
i  & i- 1\text{ is power of } 2 \\
1  & \text{otherwise}
\end{cases} = 3
$$
Therefore $n$ insertion will cost $\Phi(n)$ in the worst case.