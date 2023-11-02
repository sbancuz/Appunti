---
tags:
  - parallel_computing
---
A self organizing list is defined as a list $L$ of $n$ elements, the $Access(x)$ costs 
$$
rank_{L}(x)=dist(x,head_{L})
$$
$L$ can also be reordered by transposing adjacent elements at a cost of $1$.
### Worst case analysis

An adversary always accesses the tail element of $L$, then for any on-line algorithm $A$ we have
$$
C_{A} (S) = \Omega(|S|n)
$$
in the worst case.
### Average case analysis

Suppose that element $x$ is accessed with probability $p(x)$, then we have
$$
E[C_{A}(S)] = \sum p(x)rank_{L}(x)
$$
which is minimized when $L$ is sorted in decreasing order with respect to $p$.
### Most-used to front heuristic

The idea is to keep a count of the number of times each elements is accessed, and maintain $L$ in order of decreasing count, which means at the top we have the most accessed element. 
### Move to front heuristic

When implementing the most-used, it was found that just moving to front with a LRU approach yields  empirically good results. When accessing $x$, we transpose it to the front of the list.
$$
cos t = 2 rank_{L}(x)
$$
MTF is $4$-competitive for self-organizing list. 
#### Proof

Let $L_{i}$ be MTF 's list after the $i$-th access. Also let $c_{i}=2rank_{L_{i-1}}(x)$ the on-line cost and $\dot{c}_{i} = rank_{L_{i-1}} + t$.

We define the potential function 
$$
\Phi:\{ L_{i} \} \to R \implies \Phi(L_{i}) = 2|\{ (x,y): x \prec_{L_{i}} y \land y \prec_{\dot{L}_{i}}x  \}| = 2 \text{\# of inversions}
$$
How much does $\Phi$ change form $1$ transpose? A transposition either creates or destroys an inversion so the $\Delta\Phi = \pm2$

The amortized cost for the $i$-th operation of MTF with respect to $\Phi$ is 
$$
\begin{align}
\dot{c}_{i} &= c_{i} + \Phi(L_{i} ) - \Phi(L_{i-1})  \\
 &\leq 2r+2(|A|-|B| +t_{i}) \\
 & =4|A| + 2 +2 t_{i} \\
 & \leq 4(r^{*} + t_{i})   \\
 & = 4c_{opt} 
\end{align}
$$
where $r^{*} = |A| + |C| +1\geq|A| + 1$

>[!note]
>If we count the move towards the front as free then it becomes a $2$-competitive 