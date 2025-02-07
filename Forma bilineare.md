---
tags:
  - logica_algebra
---
Sia $V$ uno spazio vettoriale di dimensione $n$ su un campo $K$. Indichiamo con $\{ e_{1},\dots,e_{n} \}$ una base di $V$. Una funzione $f:V\times V \to K$ è detta **forma bilineare** se 
1) $f(av_{1},v_{2} ) f(v_{1},av_{2})-af(v_{1},v_{2})$
2) $f(v_{1}+v_{2},w) = f(v_{1},w) + f(v_{2}, w)$ e viceversa

Le forme bilineari sono chiuse rispetto alla somma e prodotto per scalare, infatti siano $f,f_{1},f_{2}: V\times V\to K$ delle forme bilineari. Se definiamo $f_{1}+f_{2} : V\times V \to K$ con $(f_{1}+f_{2})(v,w) = f_{1}(v,w) + f_{2}(v,w)$ e $af: V\times V \to K$ come $(af)(v,w) = af(v,w)$ allora $f_{1}+f_{2}$ e $af$ sono forme bilineari. 

Quindi l'insieme delle forme bilineari su $V$ è uno spazio vettoriale che denotiamo con il **prodotto tensoriale**
$$
V^{*} \otimes V^{*}
$$Siano $1\leq i,j \leq n$. Indichiamo con $e_{i}^{*} \otimes e_{j}^{*}$ la forma bilineare tale che
$$
e_{i}^{*} \otimes e_{j}^{*}(e_{h}, e_{k}) = \delta_{ih}\delta_{jk} 
$$
dove $\delta_{ij}$ è il delta di Kronecker (vedere la parte di #quantum  per più informazioni). L'insieme
$$
\{ e_{i}^{*} \otimes e_{j}^{*} : 1 \leq i,j \leq n \}
$$
è una base dello spazio vettoriale $V^{*}\otimes V^{*}$. Abbiamo che
$$
e_{i}^{*} \otimes e_{j}^{*} (e_{h}, e_{k}) = e_{i}^{*} (e_{h}) e_{j}^{*}(e_{k})
$$
che può essere generalizzato con $u\otimes v(x,y) = u(x)v(y) = \sum_{j}\sum_{i}u_{i}v_{j}e_{i}^{*}\otimes e_{j}^{*}$

>[!example]
>Il prodotto scalare canonico è una forma bilineare **simmetrica** su $V$ e si scrive
>$$
>e_{1}^{*}\otimes e_{1}^{*} + \dots + e_{n}^{*} \otimes e_{n}^{*}
>$$

Ad una forma bilineare $f$ su $V$ possiamo associare una matrice 
$$
M(f) \in Max_{n\times n}(K)
$$
la cui componente $M(f)_{ij}$ di coordinate $(i,j)$ è l'elemento $f(e_{i},e_{j})\in K$. In tal modo $f(u,v) = \left<  u; M(f)v \right>$

>[!example]
>La matrice del prodotto scalare è la matrice identità

Abbiamo quindi definito un isomorfismo di spazi vettoriali 
$$
M: V^{*}\otimes V^{*} \to Mat_{n\times n}(K) \qquad f \to M(f)
$$
Quindi se $A\in Mat_{n\times n}(K)$, la forma bilineare $f:V^{*}\times V^{*}$ associata ad $A$ è $f:(\text{col}_{1})\otimes e_{1}^{*} + \dots + (\text{col}_{n})\otimes e_{n}^{*}$

Essendo $V^{*}\otimes V^{*}$ lo spazio vettoriale delle forme bilineari su $V$, si ha che
1) $a(e_{i}^{*} \otimes e_{j}^{*}) = e_{i}^{*}\otimes(ae_{j}^{*})$
2) $(e_{i}^{*} + e_{j}^{*}) \otimes e_{k}^{*} = e^{*}_{i} \otimes e^{*}_{j} + e^{*}_{i} \otimes e^{*}_{k}$

Siano $V_{1},V_{2},\dots,V_{k}$ spazi vettoriali su un campo $\mathbb{F}$, una funzione
$$
f: V_{1} \times \dots \times V_{K} \to \mathbb{F}
$$
è detta **forma multilineare** se
1) $f(av_{1},\dots,v_{k}) = f(v_{1},av_{2},\dots,v_{k}) = \dots = af(v_{1}, \dots,v_{k})$
2) $f(v_{1}+w_{1}, \dots, v_{k}) = f(v_{1},\dots,v_{k}) + f(w_{1}, \dots, v_{k})$ su tutti gli elementi come prima
### Prodotto tensoriale

Siano $V_{1},\dots,V_{k}$ spazi vettoriali su un campo $\mathbb{F}$. Definiamo
$$
V_{1}^{*} \otimes  \dots \otimes  V_{k}^{*}
$$
lo spazio vettoriale delle forme multilineari.