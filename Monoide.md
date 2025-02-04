---
tags:
  - logica_algebra
aliases:
  - Monoidi
---
Un [[Insieme]] $X$ con un operazione associativa e un [[Identità]] è detto **monoide**. 

>[!example]
>a) $\mathbb{N}, \mathbb{Z}, \mathbb Q,\mathbb{R}, \mathbb{C}$ con l'addizione e identità $0$
>b) $\mathbb{N}, \mathbb{Z}, \mathbb Q,\mathbb{R}, \mathbb{C}$ con moltiplicazione e identità $1$

>[!note]
In un monoide con operazione $*$ scriveremo $xy$ invece di $x*y$

Sia $X$ un monoide. Un elemento $x\in X$ è [[Funzioni#Invertibilità|invertibile]] se esiste $y \in X$ tale che 
$$
xy = yx = e
$$
L'elemento $y$, che è **unico**, si chiama l'inverso di $x$ e lo indichiamo con $x^{-1}$

>[!note]
>L'identità di un monoide è sempre invertibile e il suo inverso è l'identità stessa

Siano $M_{1}, M_{2}$ monoidi con identità $e_{1},e_{2}$. Il **prodotto diretto** è il monoide $M_{1}\times M_{2}$ la cui identità è $(e_{1},e_{2})$ e l'operazione è definita da 
$$
(a_{1}.b_{1})(a_{2},b_{2}) = (a_{1}a_{2},b_{1}b_{2})
$$
### Sottomonoide

Sia $X$ un monoide con identità $e$. Un sottoinsieme $Y \subseteq X$ tale che $e \in Y$ e tale che è un monoide con l'operazione indotta, si dice **sottomonoide**.  Quindi se $X$ è un monoide con identità $e$ e operazione $*$, $Y$ sarà sottomonoide sse:
1) $e \in Y$
2) $a *b \in Y \qquad \forall {a,b} \in {Y}$

Sia $X$ un monoide e $S \subseteq X$ un sottoinsieme. Definiamo $\left< S \right>$ il **sottomonoide generato da $S$**  come l'intersezione di tutti i sottomonoidi di $X$ che contengono $S$. 

>[!example]
>a) $S = \{ 1 \} \subseteq (\mathbb{N}, +)$ allora $\left< \{ 1 \} \right> = \mathbb{N}$
>b) $S = \{ 0, 1 \}\subseteq (\mathbb{N}, \cdot)$ allora $\left< S \right> = S$
