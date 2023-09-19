---
tags:
  - parallel_computing
---
An algorithm is any well-defined computational procedure that takes some value, or set of values, as input and produces some value, or set of values, as output.
It must terminate in a finite number of steps.

### Analysis of algorithms

There is a need to study algorithms because:
- It helps us to understand scalability
- Performance often draws the line between feasible and impossible
- It provides a language for talking about program behavior
- Performance is the currency of computing

The running time depends on the input: an already sorted sequence is easier to sort. Generally we seek upper bounds no the running time, because everybody likes a guarantee.
- Worst case : $T(n)$ represents the maximum time of algorithm on any input size n.
- Average case : $T(n)$ represents the expected time of algorithm over all inputs of size n.
- Best case : Cheat with a slow algorithm that works fast on some input.
### $\Theta$ notation

$$
\Theta(g(n)) = \{ f(n) : 0 \leq c_{1}g(n) \leq f(n) \leq c_{2}g(n) \}
$$

$\Theta(g(n))$ measures the asymptotic performance of the function $g(n)$ in relation to the input n.

### O notation
$$
O(g(n)) = \{ f(n) : 0 \leq f(n) \leq cg(n) \}
$$
### $\Omega$ notation
$$
\Omega(g(n)) = \{ f(n) : 0 \leq cg(n) \leq f(n) \}
$$

![[Master method]]

We take insertion sort as an example
```pseudo
\begin{algorithm}
\begin{algorithmic}
	\Procedure{Insertion-sort}{$A, n$}
		\For{$j \gets 2 $ to $n$}
			\State $key \gets A[j]$
			\State $i \gets j - 1$
			\While{$i > 0 \land A[i] > key$ }
				\State $A[i + 1] \gets A[i]$
				\State $i \gets i - 1$
			\EndWhile
			\State $A[i+1] = key$
		\EndFor
	\EndProcedure
\end{algorithmic}
\end{algorithm}
```
The worst case the input is reversed and  $T(n) =\Theta(n^{2})$, the average one is still $\Theta(n^{2})$. 
Is insertion sort fast? Yes for small n but not for large n.

Take also ![[Merge sort]]

Some class of problems can be resolved through recursion with a [[Divide and conquer approach]]
