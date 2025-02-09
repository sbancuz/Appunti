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
- $m=0$ allora $\left<[0] \right> = \{ 0 \} \implies |\left< [0] \right>| = 1$
- $m>0$ e $z = \frac{mcm\{ m,n \}}{m}$
	Se adesso prendo la somma di $\sum_{z}[m] = [zm] = [mcm\{ m,n \}] = [0]$. Ovvero sto facendo $\mathbb{Z}_{n}/\mathbb{Z}_{n}$ 
	Ma se prendo la somma per $i<z$, $\sum_{i}[m] \neq [0]$ perché $i< n \implies im < zm$ e quindi abbiamo che $n$ non divide $im$. Quindi si ha che $|\left<  [m]\right>| = z$

In particolare se $MCD\{ m,n \}= 1 \iff \left< [m] \right>=\mathbb{Z}_{n} \iff z=n$; ossia l'insieme $\{ [m] \}$ genera il gruppo $\mathbb{Z}_{n}$ sse $m,n$ sono **coprimi**.

Da qui si può definire la **funzione di Eulero** come $\phi: \mathbb{N} \setminus \{ 0 \} \to \mathbb{N}\setminus \{ 0 \}$
$$
\phi(n) = \left| \{ m \leq n : MCD\{ m,n \} = 1 \} \right| 
$$
Questa funziona conta il numero di coprimi fino ad $n$.

[Teorema]
L'insieme dei sottogruppi di $(\mathbb{Z}, +)$ è $\{ n\mathbb{Z}:n \in\mathbb{N} \}$ 

>[!note]- Dimostrazione
>Sia $H \subseteq \mathbb{Z}$ un sottogruppo non banale. Sia $k=minH_{>0}$ e sia $h \in H_{>0}$ con $h \neq k$. Quindi $h>k$ e $h=nk + r$, $0 \le r \leq k$. Dunque $r=h-nk\in H \implies r=0$ per la minimalità di k.
### Gruppo ciclico

Un gruppo è **ciclico** se $G = \left< g \right>$ per qualche $g\in G$.

>[!note]
>Un gruppo ciclico è anche abeliano.

[Teorema]
Sia $G$ un gruppo ciclico. Allora ogni sottogruppo di $G$ è ciclico.

>[!note]- Dimostrazione
>Sia $g\in G$ tale che $G=\left< g \right>$. La funzione $\phi:(\mathbb{Z}, +) \to G$ definita da $\phi(n) = g^{n}$ è un morfismo suriettivo di gruppi. Abbiamo $2$ casi:
>1) $G$ è infinito $\to$ allora $Ker(\phi)=\{ 0 \}$ e quindi $\phi$ sarà anche iniettivo, e dunque isomorfo. Ogni sottogruppo di $\mathbb{Z}$ è ciclico.
>2) $G$ è finito $\to$ sia $H\subseteq G$ un sottogruppo. Allora 
>$$
>\phi^{-1}(H) = \{ n \in \mathbb{Z} : \phi(n) \in H \} \subseteq \mathbb{Z}
>$$
>è un sottogruppo di $\mathbb{Z}$, quindi esiste un $k\in \mathbb{N}$ tale che $\phi^{-1}(H) = \left< k \right>$. La restrizione $\phi:\mathbf{k}\mathbb{Z}\to H$ è un morfismo suriettivo di gruppi e $\phi(hk)=[\phi(k)]^{h}$, quindi $H = \left< \phi(k) \right>$

>[!warning]
>$(\mathbb{R}, +)$ non è ciclico perché non esiste un biiezione $\underbrace{ \mathbb{R} }_{ \text{continuo} } \simeq \underbrace{ \mathbb{Z} }_{ \text{numerabile} }$

[Corollario]
L'insieme dei sottogruppi di $\mathbb{Z}_{n}$ è $\{ \left< [m]\right> : [m] \in \mathbb{Z}_{n} \}$

[Teorema]
Sia $n \in \mathbb{N}$ e sia $d | n$ ($d$ divide $n$). Allora esiste al più un unico sottogruppo di $\mathbb{Z}_{n}$ di cardinalità $d$.

>[!note]- Dimostrazione
>Sia $H \subseteq \mathbb{Z}_{n}$ sottogruppo tale che $|H|=d$ si considerino le proiezioni canoniche
>$$
>\mathbb{Z} \xrightarrow{\pi_{1}} \mathbb{Z_{n}} \xrightarrow{\pi_{2}} \mathbb{Z}_{n} /H
>$$
>Poiché $\pi_{1}^{-1}(H) = \{ m \in \mathbb{Z} : \pi_{1}(m) \in H \} = Ker(\pi_{2} \circ\pi_{1})$ è un sottogruppo di $\mathbb{Z}$ allora esiste $k\in \mathbb{N}$ tale che $\pi^{-1}(H) = k\mathbb{Z}$.  Quindi essendo $\pi_{2} \circ\pi_{1}$ un morfismo suriettivo di gruppi
>$$
>\mathbb{Z}_{n} /H \simeq \mathbb{Z}/\pi^{-1}(H) = \mathbb{Z} /k\mathbb{Z} = \mathbb{Z}_{k}
>$$
>Ossia $k$ è univocamente determinato e allora $H=\pi_{1}(k\mathbb{Z})$ è univocamente determinato.



