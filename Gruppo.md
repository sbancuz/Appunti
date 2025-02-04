---
tags:
  - logica_algebra
aliases:
  - Gruppi
---
Un [[Monoide]] i cui elementi sono tutti invertibili è chiamato gruppo. Se l'operazione è commutativa, il gruppo è chiamato [[Gruppo abeliano]].

>[!example]
>a) $(P(X), \triangle)$ è un gruppo abeliano con identità $\emptyset$ e l'inverso è l'identità stessa
>b) $(\mathbb{Z}, +), (\mathbb{Q}, +), (\mathbb{R}, +),(\mathbb{C}, +)$ sono tutti abeliani
>c) Sia $X = \{ 1,2,\dots, n \}$. L'insieme delle funzioni invertibili $f: X \to X$ è il *gruppo delle permutazioni* di $n$ elementi. Lo indichiamo con $S_{n}$ ed ha cardinalità $|S_{n}| = n!$; non è abeliano per $n \geq 3$ visto che perde la commutatività

Siano $M_{1}, M_{2}$ gruppi con identità $e_{1},e_{2}$. Il **prodotto diretto** è il gruppo $M_{1}\times M_{2}$ la cui identità è $(e_{1},e_{2})$ e l'operazione è definita da 
$$
(a_{1}.b_{1})(a_{2},b_{2}) = (a_{1}a_{2},b_{1}b_{2})
$$
In tal caso se $(g_{1},g_{2})\in G_{1}\times G_{2}$, il suo inverso è $(g_{1},g_{2})^{-1} = (g_{1}^{-1}, g_{2}^{-1})$
### Sottogruppo

Sia $G$ un gruppo. Un sottoinsieme $H \subseteq G$ tale che è un gruppo con l'operazione indotta, si dice **sottogruppo**. Quindi un sottoinsieme $H \subseteq G$ di un gruppo $G$ è un sottogruppo se:
1) $h^{-1} \in H \quad \forall {h} \in {H}$
2) $h_{1}h_{2} \in H$

Se $e$ è l'identità di un gruppo $G$, l'insieme $\{  e\} \subseteq G$ è detto **sottogruppo banale**.

Sia $X$ un gruppo e $S \subseteq X$ un sottoinsieme. Definiamo $\left< S \right>$ il **sottogruppo generato da $S$**  come l'intersezione di tutti i sottogruppo di $X$ che contengono $S$. 

Si consideri il gruppo $\mathbb{Z}_{n} = (\{ [0],\dots,[n-1] \}, +)$ e siano $m,n \in \mathbb{N}$ con $m<n$. Se
- $m=0$ allora $\left<[0] \right> = \{ 0 \}$
- $m>0$ e $z = \frac{mcm\{ m,n \}}{m}$ allora $[zm] = [mcm\{ m,n \}]=[0]$

---
