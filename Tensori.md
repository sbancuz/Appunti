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
dove $T_{i}$ sono tensori di rango $1$.