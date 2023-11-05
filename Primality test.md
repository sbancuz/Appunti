---
tags:
  - parallel_computing
  - coding
---
The naive approach for testing if a number is prime is
```pseudo
\begin{algorithm}
\begin{algorithmic}
\Procedure{IsPrime}{$n$}
	\If{$n = 2$} 
		\Return \True
	\EndIf
	\If{isEven($n$)} 
		\Return \False
	\EndIf
	\For{$i = 1$ to $\sqrt{n/2}$}
		\If{divides($2i + 1$, $n$)}
			\Return \False
		\EndIf
	\EndFor
	\Return \True
\EndProcedure
\end{algorithmic}
\end{algorithm}
```

$T(n) = \Theta(\sqrt{  n})$
### Fermat little theorem

If $p$ prime and $0<a<p$, then $a^{p-1}\text{mod } p = 1$
```pseudo
\begin{algorithm}
\begin{algorithmic}
\Procedure{CanBePrime}{$n$}
	\State $z \gets 2^{n-1}$mod$n$
	\If{$z = 1$}
		\Return \True
	\Else
		\Return \False
	\EndIf
\EndProcedure
\end{algorithmic}
\end{algorithm}
```

The randomized approach works in polynomial time, if the answer is not prime then it's not prime but when it says that it is i could be wrong with a probability of $p > 0$. This approach works modifying the base $\in [2, n-1]$ to calculate $z$.
### Carmichael numbers

A number $\geq 2$ is a Carmichael number iff $n$ is composite and for any $a$ with $GCD(a, n) = 1$ we have $a^{p-1}\text{mod } p = 1$
### Theorem

If $p$ prime and $0<a<p$ then the only solutions for the equation $a^{2}\text{mod } p = 1$  are $a = 1$ and $a = n-1$.
$a$ is called a non-trivial square root if $a^{2}\text{mod } p = 1$ for $a \ne 1,n-1$

Now the idea is during the computation of $a^{n-1}$ to check if the number is a non trivial square root.
```pseudo
\begin{algorithm}
\begin{algorithmic}
\State isProbablyPrime $\gets$ \True
\Procedure{powerWithCheck}{$a, p, n$}
	\If{$p = 0$}
		\Return 1
	\EndIf
	\State $x \gets $powerWithCheck($a, p/2, n$)
	\State $res \gets x \times x$ mod $ n$
	\If{$res =  1 \land x \ne 1 \land x \ne n - 1$}
		\State isProbablyPrime $\gets$ \False
	\EndIf
	\If{$p$ mod $2 = 1$}
		\State $res \gets a \times res$ mod $n$
	\EndIf
	\Return $res$
\EndProcedure
\end{algorithmic}
\end{algorithm}
```
An example of an application of these algorithms are [[RSA Cryptosystem]]
