---
tags:
  - logica_algebra
---
Sia $A$ un [[Anello]] commutativo. Un sottoinsieme $I \subseteq A$ è detto **ideale** se
1) $I$ è un [[Gruppo#Sottogruppo]] di $(A, +)$
2) $ax \in I \quad \forall {a} \in {A}, x\in I$

>[!example]
>Gli interi pari formano un ideale nell'anello $\mathbb{Z}$. $n\mathbb{Z}$ è un ideale di $\mathbb{Z}$, $\forall {n} \in {\mathbb{N}}$, e tutti gli ideali di $\mathbb{Z}$ sono di questo tipo.

Siano $I,J \subseteq A$ ideali di un anello commutativo $A$ allora
1) $I\cap J$ è un ideale di $A$
2) $I + J = \{ x+y : x\in I, y \in J \}$ è ideale di $A$
3) $IJ = \left< \{ xy : x \in I, y \in J \} \right>$ è ideale di $A$

Sia $S \subseteq A$ un sottoinsieme di un anello commutativo. L'ideale generato da $S$ è l'intersezione di tutti gli ideali di $A$ contenenti $S$ e si indica con $\left< S \right>$. Se $S = \{  x \}$ -- contiene un solo elemento -- diciamo che $\left< S \right>$ è **l'ideale principale generato** da $x\in A$.

>[!example]
>Gli ideali di $\mathbb{Z}$ sono tutti principali visto che $n\mathbb{Z} = \left<  [n]\right>$ che contiene solo $[n]$

Un anello i cui ideali sono tutti principali si dice **anello ad ideali principali**.

[Teorema]
Sia $A$ un [[anello]] commutativo e $I \subseteq A$ un ideale. Allora
1) $I =A$ sse $I$ contiene un elemento invertibile
2) $A$ è un [[Campo]] sse i suoi unici ideali sono $\left< 0 \right>, A=\left< 1_{A} \right>$

>[!note]- Dimostrazione 1
>$\implies$
> Se $I =A$ allora $1_{A}\in A$ e $1_{A}$ è invertibile. 
>
>$\impliedby$
> Sia $u\in I$ un elemento invertibile. Allora $u^{-1}\in A$ e quindi $1_{A}=uu^{-1}\in I$. Ne segue che $A = \left< 1_{A} \right> \subseteq I$ e quindi $I=A$

>[!note]- Dimostrazione 2
>$\implies$
>Sia $A$ un campo e sia $I\neq\left< 0 \right>$. Se $x \in I$ e $x \neq 0$ allora $x$ è invertibile e quindi $I =A$ per $(1)$. 
>
>$\impliedby$
>Viceversa, se $\left< 0 \right>$ e $A$ sono gli unici ideali di $A$, e se $x\in A \setminus \{ 0 \}$, abbiamo $I = \{ ax | a \in A \}$ ovvero $\left< x \right>=\left< 1_{A} \right>$, ossia $ax =1_{A}$ per qualche $a \in A$. Quindi $x$ è invertibile.

