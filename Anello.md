---
tags:
  - logica_algebra
aliases:
  - Anelli
---
Sia $X$ un insieme su cui sono definite due operazioni $+$ e $\cdot$. $X$ è un anello con unità $1_{x}$ se 
1) $(X,+)$ è un [[Gruppo]] abeliano
2) $(X, \cdot)$ è un [[Monoide]] con identità $1_{x}$
3) Valgono le proprietà distributive

Diciamo che un anello $X$ è **commutativo** se il monoide lo è. Indichiamo con $0$ l'identità del gruppo $(X, +)$ . Confideremo sempre $0\neq 1_{A}$ e in questo corso studieremo solo anelli commutativi con unità. 

Sia $A$ un anello commutativo. Un elemento $x\in A$ è detto **zero-divisore** se esiste $y\in A\setminus \{ 0 \}$ tale che
$$
xy = 0
$$
Diciamo che un elemento $x\in A$ è **invertibile** se è un elemento invertibile del monoide $(A, \cdot)$

[Teorema]
Sia $A$ un anello commutativo; allora l'insieme degli elementi invertibili di $A$ è disgiunto dall'insieme degli zero-divisori di A.

>[!note]- Dimostrazione
>Siano $x,y\in A$ tali che $xy=0$. Se $x$ è invertibile, allora $x^{-1}xy=y=0$. Quindi $x$ non è zero divisore.

[Teorema - Legge di cancellazione]
Sia $A$ un anello commutativo e sia $x\in A$ un elemento che non è uno zero-divisore; allora 
$$
xy = xz \implies y =z \quad \forall {y,z} \in  {A} 
$$
[[Campo]]
### Anello quoziente

Sia $A$ un anello commutativo e $I \subseteq A$ un ideale. In particolare, $A$ con l'operazione $+$ è un [[Gruppo]] abeliano e $I$ è un sottogruppo di $A$. Allora possiamo definire il gruppo quoziente $A /I$ con l'operazione
$$
[x][y] = [xy] \quad \forall {[x][y]} \in {A} 
$$
abbiamo che $A /I$ è un anello commutativo con unità $[1_{A}]$. Infatti, prendendo $x'\in[x], y'\in[y]$ esistono $i_{x},i_{y}\in I$ tali che
$$
x' = x+ i_{x} \quad y' = y + i_{y}
$$
quindi
$$
x'(y)' = (x + i_{x})(y + i_{y}) = xy + \underbrace{ x+i_{x} + yi_{y} + i_{y}i_{x} }_{ \in I \text{ perché } I \text{ è un ideale di }A }
$$
e infine $[x'y'] = [xy]$. Possiamo anche dire che per ogni $[1_{A}]$ è l'unità di $A /I$.