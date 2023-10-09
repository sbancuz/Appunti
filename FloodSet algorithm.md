---
tags:
  - distributed_systems
  - coding
---
This algorithm is used to decide the result of a request processed by a group of processes. This is a method for [[Fault tolerance]] for synchronous systems.

```pseudo
\begin{algorithm}
\begin{algorithmic}
\Procedure{FloodSet}{$P$}
	\State $v0 \gets $ defaultVal
	\State $W \gets \{v0\}$
	\For{$i \gets f + 1$}
		\State send($P[i], W$)
		\State $W \gets W \cup$ received($W$)
	\EndFor
	\If{$|W| = 1$}
		\Return decided($W$)
	\Else
		\Return $v0$
	\EndIf
\EndProcedure
\end{algorithmic}
\end{algorithm}
```

>[!note]
The received function is asynchronous, this means that the result of the other process may arrive at any time but the system remains inherently synchronous

