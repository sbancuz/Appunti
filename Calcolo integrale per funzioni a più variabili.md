---
tags: analisi_2
---
### [[Calcolo integrale]] di linea

Sia $\underline{r}:[a,b] \subseteq \mathbb R\to \mathbb R^n$ una curva regolare con sostegno $\gamma$ e sia $f$ una funzione continua a valori reali definita su un sottoinsieme $A$ di $\mathbb R^n$ contenete $\gamma$ si dice integrale di linea di $f$ il numero
$$
\int _{\gamma}f \, ds = \int _{a}^{b}f(\underline{r}(t))||\underline{r}'(t)|| \, dt  
$$

>[!tip] Applicazioni
>- Massa => $M = \int _{\gamma}f \, ds$
>- Baricentro => $B_{i} = \frac{1}{M}\int _{a}^{b} r_{i}(t) \rho(\underline{r}(t))||\underline{r}'(t)||\, dt$

L'integrale di linea fornisce l'area della superficie tra $\gamma$ e $Gr_{f}$

### Integrale multiplo

L'integrale multiplo su insiemi $A$ k-dimensionali con $k>1$ con notazione
$$
\int _{A}f(\underline{x}) \, d\underline{x} 
$$
calcola il volume della regione racchiusa tra il dominio $A$ della funzione e $Gr_{f}$ un analogia al caso ad una variabile

### Integrale doppio

Sia $k=2$. L'integrale multiplo viene chiamato integrale doppio. 
$$
\iint_{D}f \ dxdy = \int _{D}f \, d\underline{x} 
$$
Iniziamo col definire alcune regioni $D\subseteq \mathbb{R}^{2}$ adatte all'integrazione:
- y-semplice se è del tipo
$$
D= \{ (x,y)\in \mathbb{R}^{2} : x\in [a,b], g_{1}(x)\leq y\leq g_{2}(x) \}
$$
dove $a,b\in \mathbb{R}$ con $a<b$ e $g_{1},g_{2}:[a,b] \to \mathbb{R}$ sono funzioni tali che:
1) $g_{1},g_{2}$ sono continue
2) $g_{1}\leq g_{2} \forall {x} \in {[a,b]}$
$$
Area(D) = \int _{a}^{b} g_{2}(x) \, dx - \int _{a}^{b}g_{1}(x) \, dx  = \int _{a}^{b}g_{2}(x)-g_{1}(x) \, dx 
$$
>[!note]
>Possiamo vedere la regione $D$ come unione di segmenti verticali, uno per ogni $x\in[a,b]$


- x-semplice se è del tipo
- $$
D= \{ (x,y)\in \mathbb{R}^{2} : y\in [c,d], h_{1}(x)\leq x\leq h_{2}(x) \}
$$
dove $c,d\in \mathbb{R}$ con $c<d$ e $h_{1},h_{2}:[c,d] \to \mathbb{R}$ sono funzioni tali che:
1) $h_{1},h_{2}$ sono continue
2) $h_{1}\leq h_{2} \forall {y} \in {[c,d]}$

>[!note]
>Possiamo vedere la regione $D$ come unione di segmenti orizzontali, uno per ogni $y\in[c,d]$

### Spazi regolari in $\mathbb{R}^{2}$

$E\subseteq \mathbb{R}^{2}$ si dice regolare se è un'unione finita di insiemi $x$-semplici e $y$-semplici

### Integrabilità funzioni continue

Sia $D\subseteq \mathbb{R}^{2}$ un insieme regolare e sia $f:D\to \mathbb{R}$ una funzione continua in $D$ allora $f$ è integrabile in $D$

### Formule di riduzione

Sia $D$ un dominio $y / x$-semplice e sia $f:D\to \mathbb{R}$ una funzione continua in $D$ allora abbiamo che
$$
\iint_{D}f(x,y)  \ dxdy = \int _{a}^{b}\left( \int _{g_{1}(x)}^{g_{2}(x)} f(x,y) \, dy  \right) \, dx 
$$

### Integrale triplo

Sia $k=3$, allora l'integrale multiplo si dice triplo. Tutto ciò fatto per $k=2$ si estende per $k>2$

### Teorema di integrazione per fili

Sia $\Omega \subseteq \mathbb{R}^{3}$ un insieme rappresentabile nella funzione 
$$
\Omega =\{ (x,y,z)\in \mathbb{R}^{3} : (x,y)\in D, l_{1}(x,y)\leq z\leq l_{2}(x,y)\}
$$
dove $D$ è una regione regolare nel piano $xy$ e $l_{1},l_{2}$ continue con $l_{1}\leq l_{2}$

Se $f:\Omega\to \mathbb{R}$ è continua, allora $f$ è integrabile su $\Omega$ e l'integrale si può calcolare con la formula
$$
\iiint _{\Omega}f(x,y,z) \ dxdydz = \iint _{D}\left( \int _{l_{1}(x,y)}^{l_{2}(x,y)}f(x,y,z) \, dz  \right) \ dxdy
$$

### Integrazione a strati

Sia $\Omega \subseteq \mathbb{R}^{3}$ rappresentabile nella forma
$$
\Omega = \{ (x,y,z)\in\mathbb{R}^{3} : z_{1}\leq z\leq z_{2}, (x,y)\in D(z) \}
$$
l'insieme $D(z)$ detto strato è un dominio regolare del piano. Se $f$ è continua, allora $f$ è integrabile su $\Omega$ e
$$
\iiint _{\Omega}f(x,y,z) \ dxdydz = \int _{z_{1}}^{z_{2}}\left( \iint _{D(z)}f(x,y,z) \ dxdy \right)  \, dz 
$$

>[!note]
>Gli integrali doppi e tripli godono delle stesse proprietà basilari degli integrali normali come linearità, monotonia, annullamento e additività


### Cambiamento di variabili

Sia $n=2,3$. Chiamiamo cambiamento di variabili tra due regimi $U$ e $V$ in $\mathbb{R}^{n}$ ogni [[Diffeomorfismo]]

### Teorema dell'inversione locale