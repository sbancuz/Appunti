---
tags:
  - logica_algebra
---
Sia $X$ un insieme. Un sottoinsieme $R \subseteq X \times X$ si dice **relazione** su $X$. Una relazione può essere:
1) riflessiva $\to$ $(x,x) \in R \quad \forall {x} \in {X}$
2) simmetrica $\to$ $(x,y)\in \implies (y,x) \in R \quad \forall {x,y} \in {R}$
3) transitiva $\to$ $(x,y) \in R, (y, z) \in R \implies (x,z) \in R \quad \forall {z,y,x} \in  {X}$
4) antisimmetrica $\to$ $(x,y)\in R, (y,x)\in R \implies x= y, \forall {x,y} \in {X}$

Se una relazione soddisfa $1,2,3$ allora è detta **relazione di equivalenza** e si indica con $x \sim y$. Sia $x\in X$ e $R$ una relazione di equivalenza su $X$, l'insieme 
$$
[x] = \{ y \in X : x \sim y\}
$$
è detto **classe di equivalenza** di $x$. L'insieme
$$
X\diagup{\sim}  = \{ [x] : x \in X \} \quad \begin{align}
\pi : & X \to X \diagup{\sim} \\
 & x \to [x]
\end{align}
$$
e la funzione $\pi$ è detta la **proiezione canonica**.

Siano $x,y\in X$ allora se $x\sim y$ abbiamo che $[x] =[y]$. Se $x \nsim y$ abbiamo che $[x] \cap[y] = \emptyset$. Quindi 
$$
X = \bigcup_{[x] \in X\diagup{\sim}}[x]
$$
ossia $X\diagup{\sim}$ è una partizione di $X$

Sia $G$ un [[Gruppo]] e $H\subseteq G$ un sottogruppo. La relazione $\sim$ su $G$ definita da
$$
g_{1}\sim g_{2}  \equiv g_{1}=g_{2}h
$$
è di equivalenza. Quindi si ha che
5) $g\sim g: g=ge \quad \forall {g} \in {G};e\in H$
6) $g_{1}\sim g_{2} \implies g_{2}\sim g_{1} : g_{1}=g_{2}h \implies g_{1}h^{-1}=g_{2}$
7) $g_{1}\sim g_{2},g_{2}\sim g_{3} \implies g_{1}\sim g_{3} : g_{1}=g_{2}h. g_{2}=g_{3}h' \implies g_{1} = g_{3} \underbrace{ hh' }_{ \in H } =g_{3}h''$
In questo caso l'insieme quoziente lo indichiamo con $G\diagup{H}$. Se $G$ è abeliano, possiamo definire la seguente operazione 
$$
G\diagup{H} : [g_{1}] + [g_{2}] = [g_{1} + g_{2}]
$$
La classe $[0]$ dell'identità di $G$ è l'identità di $(G\diagup{H}, +)$. Inoltre l'inverso è $-[g] = [-g]$

>[!example]
>Sia $G=(\mathbb{Z}, +)$ e $n\in\mathbb{N}$. Il sottoinsieme $n\mathbb{Z} = \{ kn : k\in \mathbb{Z} \}$ è un sottogruppo di $\mathbb{Z}$. Definiamo il gruppo abeliano 
>$$
>\mathbb{Z}_{n} = \mathbb{Z} \diagup{n\mathbb{Z}} \qquad \mathbb{Z}_{0} = \mathbb{Z}\diagup{\{ 0 \}}\simeq \mathbb{Z}
>$$
>Siano $x,y\in \mathbb{Z}$ allora $x\sim y$ sse $x = y + h$ con $h \in n\mathbb{Z}$. Allora $x-y = kn$ per qualche $k \in \mathbb{Z}$ ed il resto della divisione di $x$ per $n$ è uguale al resto della divisione di $y$ per $n$. 
>In generale si ha che  $\mathbb{Z}_{n} = \{ [0],\dots,[n-1] \}$

Sia $G$ un gruppo abeliano e $H \subseteq G$ un sottogruppo. La proiezione canonica 
$$
\pi: G\to G\diagup{H}
$$
è un morfismo suriettivo di gruppi. Se è anche finito allora 
$$
[g] \in G\diagup{H} \implies |[g]| = |H|
$$
Poiché le classi di equivalenza sono una partizione di $G$, abbiamo 
$$
|G| = |G\diagup{H}|\cdot |H|
$$
In particolare, la cardinalità (o **ordine**) di un sottogruppo di un gruppo finito divide la cardinalità del gruppo.
