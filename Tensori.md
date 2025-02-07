---
tags:
  - logica_algebra
---
Siano $V_{1}, \dots, V_{h}$ spazi vettoriali su un [[Campo]] $K$ con basi $\{ v_{1}^{1},\dots,v_{i_{1}}^{1} \}, \dots, \{ v_{1} ^{h}, \dots, v_{i_{h}}^{h}\}$ allora 
$$
V_{1}\otimes V_{2}\otimes  \dots V_{K} 
$$
è lo spazio vettoriale con base $\{ v_{j_{1}}^{1} \otimes \dots \otimes v_{j_{h}}^{h} : 1 \leq j_{1} \leq i_{1}, \dots, 1\leq j_{h} \leq i_{h} \}$ che soddisfa:
1) $a(v_{j_{1}}^{1} \otimes \dots \otimes v_{j_{h}}^{h}) = av_{j_{1}}^{1} \otimes \dots \otimes v_{j_{h}}^{h} = v_{j_{1}}^{1} \otimes \dots \otimes av_{j_{h}}^{h}$
2) $(v_{1} + w_{1}) \otimes \dots \otimes v_{h} = v_{1} \otimes \dots \otimes v_{h} + w_{1} \otimes \dots \otimes v_{h}$ che vale anche nelle altre posizioni
L'insieme $\{ v_{1} \otimes \dots \otimes v_{h} : v_{i} \in V_{i}, \forall {1 \leq i \leq h}  {} \}$ è detto l'insieme dei **tensori** di rango $1$.

Ogni elemento di $V_{1}\otimes V_{2}\otimes  \dots V_{K}$ si scrive come combinazione lineare di tensori di rango $1$, infatti la sua base è costituita da tensori di rango uno. Sia $T\in V_{1}\otimes V_{2}\otimes  \dots V_{K}$, definiamo il **rango del tensore** e lo chiamiamo $rk(T)$ il numero $r\in \mathbb{N}$ tale che
$$
T = \sum T_{i}
$$
dove $T_{i}$ sono tensori di rango $1$. Poiché $dim(\otimes_{i}^{h} v_{i}) = \prod_{i}^{h}di m(V_{i})$ abbiamo che se $\ni T$ allora
$$
rk(T) \leq  \prod_{i}^{h}di m(V_{i})
$$
Adesso verifichiamo che la nozione di rango di un tensore è coerente con quella di rango di una matrice, quindi interpretando una matrice come [[Forma bilineare]], e quindi come un tensore. Vediamo subito che una matrice di rango $1$ corrisponde ad un tensore di rango $1$. Una matrice $m\times m$ di rango $1$ ha come colonne multipli di un qualche vettore $v\in K^{m}\setminus \{ 0 \}$. Con colonne $a_{1}v, \dots, a_{n}v$. Quindi tale matrice di rango $1$ si può scrivere come prodotto di $2$ vettori $a,v$; in forma bilineare, è il seguente elemento
$$
(v_{1}e_{1}^{*} + \dots + v_{m}e_{m}^{*}) \otimes  (a_{1}e_{1}^{*} + \dots + a_{n}e_{n}^{*})
$$
dunque la matrice $A\in Mat_{m\times n}(K)$ tale che $rk(A) = 1$ corrisponde ad un tensore tale che $rk(T_{A}) = 1$.

Dalla caratterizzazione del rango di una matrice in termini di combinazioni lineari di matrici di rango $1$, e dalla definizione di rango di un tensore, segue che le matrici di rango $r$ in $Mat_{m \times n}(K)$ stanno in corrispondenza biunivoca con i tensori di rango $r$.

Sia $V$ uno spazio vettoriale su un campo $K$ con base canonica. Gli elementi di $V^{*}\otimes V = span\{ e_{i}^{*}\otimes e_{j} \}$ possono essere interpretati come endomorfismi di $V$ nel seguente modo
$$
e_{i}^{*} \otimes  e_{j}(e_{h}) = e_{i}^{*}(e_{h})e_{j}
$$
Se $f\in End(V)$ è rappresentato dalla matrice $A$, allora come elemento di $V^{*} \otimes V$
$$
f = e_{1}^{*}\otimes (a_{11}e_{1} + \dots + a_{n1}e_{n}) + \dots + e_{n}^{*}\otimes (a_{1n}e_{1} + \dots + a_{nn}e_{n})
$$
viceversa, ogni elemento di $V^{*}\otimes V$ può essere interpretato come un endomorfismo di $V$ e tale corrispondenza biunivoca è un isomorfismo di spazi vettoriali
$$
End(V) \to V^{*} \otimes  V
$$
In generale, i [[Morfismo]] di spazi vettoriali $f:V\to W$ sono in corrispondenza biunivoca con $V^{*} \otimes W$ e tale corrispondenza è un isomorfismo di spazi vettoriali
$$
Hom(V,W) \to V^{*} \otimes  W
$$
Il rango di un morfismo corrisponde al rango del tensore $f\in V^{*}\otimes W$.

Adesso andiamo a considerare la moltiplicazione di matrici $2\times 2$. Questa è una forma bilineare $M_{2,2,2}(A,B)=AB$ e possiamo verificare sia bilineare perché
1) $x(AB) = (xA)B=A(xB)$
2) $A(B_{1}+B_{2}) = AB_{1} + AB_{2}, (A_{1} + A_{2})B = A_{1}B + A_{2}B$

>[!note]
>È possibile generalizzare questo risultato ad $n$ elementi

