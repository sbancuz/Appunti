---
tags:
  - compilers
---
This is an algorithm that constructs a [[Finite state automata]] from a regex constructing a deterministic recognizer without spontaneous moves.

To do so, it transforms the generic regex to a numbered one by applying a running index to each of them. Consider the end marked regex $e$  $┤$ instead of the original regex $e$. We define the set $FOL(c_{\#})$ of the followers of $c_{\#} \in \Sigma_{\#}$

![[non ho voglia di copiare.png]]

```pseudo
\begin{algorithm}\begin{algorithmic}
\State $q_0 \gets Ini(e_\# ┤)$
\State $Q \gets \{q_0\}$
\State $\delta \gets \emptyset$
\While{$\exists q \in Q \land $ isUnmarked($q$)}
	\State mark($q$)
	\For{$e \in \Sigma$}
		\State $q' \gets \cup_{c_\# \in \Sigma^* \in q} Fol(c_\#)$
		\If{$q' \ne \emptyset$}
			\If{$q' \notin Q$}
				\State unmark($q'$)
				\State $Q \gets Q \cup \{q'\}$
			\EndIf
			\State $\delta \gets \delta \cup \{q \to q'\}$
		\EndIf
	\EndFor
\EndWhile
\end{algorithmic}\end{algorithm}
```

The algorithm examines the states, and constructs their destination states and outgoing moves, by the subset construction.

>[!note]
>This algorithm can also be used to determinize a non-deterministic automaton

