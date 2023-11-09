---
tags:
  - parallel_computing
---

Treaps achieve the same time bounds as other auto balancing tree, but they do not require any balancing information. The idea behind them is to assign a priority to any element $x$ at random in an uniform way.

A treap is actually a binary tree implemented as a heap. Each node contains one element with $key(x)$ and $prio(x)$ with the lowest priority is put at the top of this tree.

For each element $x$:
- elements $y$ in the left subtree $x$ satisfy: $key(y)<key(x)$
- elements $y$ in the right subtree $x$ satisfy: $key(y)>key(x)$
- if $y$ is a child of $x$ then $prio(y)>prio(x)$

>[!Lemma]
>
For elements $x_{1},\dots,x_{n}$ with $key(x_i)$ and $prio(x_{i})$, there exists a unique treap.

The search tree has the structure that would result if elements were inserted in the order of their priorities.

The search algorithm is the same as the one in a normal BST with it's time [[Complexity of an algorithm]] of $O(\#elements)$ and it grows with $O(\log n)$
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{Search}{$root, k$}
	\State $v \gets root$
	\While{$v \ne nil$}
		\If{$key(v) = k$}
			\Return $v$
		\Elif{$key(v) \lt k$}
			\State $v \gets $rightChild($v$)
		\Elif{$key(v) \gt k$}
			\State $v \gets $leftChild($v$)
		\EndIf
	\EndWhile
	\Return $nil$
\EndProcedure
\end{algorithmic}\end{algorithm}
```

>[!lemma]
>Let $P_{min}(M) = min(prio(M_{x}))$ and $x_{i}$ the i-th smallest key then
>- let $i<m$. $x_{i}$ is ancestor of $x_{m}$ iff $P_{min}(\{x_{\mathbf{i}}\dots,x_{m}\}) = x_{i}$ 
>- let $m<i$. $x_{i}$ is ancestor of $x_{m}$ iff $P_{min}(\{x_{\mathbf{m}}\dots,x_{i}\}) = x_{i}$ 

The insertion works as follows:
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{Insert}{$root, x$}
	\State $prio \gets $rand()
	\State $pos \gets $Search($root, x$)
	\State $v \gets$ makeLeaf($pos, x$)
	\While{$prio(parent(x)) > prio(x)$}
		\If{isLeftChild($key(v))$}
			\State rotateRight($parent(x))$
		\Else
			\State rotateLeft($parent(x))$
		\EndIf
	\EndWhile
\EndProcedure
\end{algorithmic}\end{algorithm}
```
The deletion is:
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{Delete}{$root, x$}
	\State $pos \gets $Search($root, x$)
	\While{$\lnot $isLeaf($root, x$)}
		\State $u \gets$ smallestPrio($pos$)
		\If{isLeftChild($u$}
			\State rotateRight($parent(x))$
		\Else
			\State rotateLeft($parent(x))$
		\EndIf
	\EndWhile
	\State Delete($x$)
\EndProcedure
\end{algorithmic}\end{algorithm}
```
>[!lemma]
>The worst case in both insert and delete is $O(\log n)$ but in the average case the expected number of rotations is 2

The split operation is defined as 
$$
split(T, k, T_{1}, T_{2}):=\forall {x_{1}} \in {T_{1}}, x_{2}\in T_{2}: key(x_{1})\leq k \land k < key(x_{2})
$$

If $k$ is in $T$, delete it and the re-insert after into $T_{1}$. This operation is implemented as
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{Split}{$T, k, T_1, T_2$}
	\State $x \gets $ newNode($key = k, prio = -\infty$)
	\State Insert($T, x$)
	\State $T_1 \gets left(T)$
	\State $T_2 \gets right(T)$ 
	\State Delete($T, root(T)$)
\EndProcedure
\end{algorithmic}\end{algorithm}
```
And the union is
$$
union(T_{1}, T_{2}):=\forall {x_{1}} \in {T_{1}}, x_{2}\in T_{2}: key(x_{1}) < key(x_{2})
$$
```pseudo
\begin{algorithm}\begin{algorithmic}
\Procedure{Union}{$T_1, T_2$}
	\State $k \gets $ middleKey($T_1, T_2$)
	\State $x \gets $ newNode($key = k, prio = -\infty$)
	\State Insert($T, x$)
	\State Delete($T, x$)
\EndProcedure
\end{algorithmic}\end{algorithm}
```
>[!note]
>The $middleKey$ op is such that $key(x_{1})<k<key(x_{2}) \forall {x_{1}x_{2}} \in {T_{1}T_{2}}$

The expected running time of these 2 operations is $O(\log n)$
