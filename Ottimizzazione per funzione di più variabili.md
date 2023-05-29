---
tags: analisi_2
---
### Derivate parziali seconde

Partiamo dal caso $n=2$, siano $A\subseteq \mathbb{R}^{2}$ aperto e $f: A\to \mathbb{R}$ derivabile in $A$ con derivate parziali $f'_{x}$ e $f'_{y}$ anch'esse derivabili in $A$.
Definiamo le derivate seconde parziali come
$$
\begin{align}
f_{x^{2}}  & = \frac{ \partial^{2} f }{ \partial x^{2} } = \frac{ \partial  }{ \partial x } \left( \frac{ \partial f }{ \partial x } \right) (x,y) \\
f_{y^{2}}  & = \frac{ \partial^{2} f }{ \partial y^{2} } = \frac{ \partial  }{ \partial y } \left( \frac{ \partial f }{ \partial y } \right) (x,y) \\
f_{xy}  & = \frac{ \partial^{2} f }{ \partial x\partial y } = \frac{ \partial  }{ \partial x } \left( \frac{ \partial f }{ \partial y } \right) (x,y) \\
f_{yx}  & = \frac{ \partial^{2} f }{ \partial y \partial x } = \frac{ \partial  }{ \partial y } \left( \frac{ \partial f }{ \partial x } \right) (x,y) 
\end{align}
$$
Diciamo che $f$ è derivabile due volte in $(x_{0},y_{0})\in A$ se esistono le $4$ derivate parziali seconde, in più se è derivabile due volte in ogni punto di $A$ allora si dice che è derivabile due volte in $A$

### Matrice Hessiana

Se $f$ è derivabile due volte in $(x_{0},y_{0})$ allora definiamo la matrice Hessiana di $f$ in $(x_{0},y_{0})$ come
$$
H_{f} (x_{0},y_{0}) = \left( \begin{matrix}
f_{x^{2}} (x_{0},y_{0}) & f_{yx} (x_{0},y_{0})  \\
f_{xy} (x_{0},y_{0})   &  f_{y^{2}} (x_{0},y_{0}) 
\end{matrix} \right)  = \left( \begin{matrix}
\triangledown f_{x} \\
\triangledown f_{y}
\end{matrix} \right) 
$$

Se tutte le derivate parziali seconde sono continue in $A$ allora si dice che $f$ è di classe $\mathcal C^{2}$ in $A$

La "versione" a n variabili è la Jacobiana

### Teorema di Schwarz

Sia $A\subseteq \mathbb{R}^{2}$ aperto e $f\in\mathcal C^{2}(A)$ allora
$$
f_{xy}(x,y) = f_{yx} (x,y)
$$
cioè la matrice Hessiana è simmetrica.

### Formula di Taylor al secondo ordine

==> [[Serie di Taylor]]

Sia $A\subseteq \mathbb{R}^{2}$ aperto e $f\in\mathcal C^{2}(A)$ allora
$$
f(\underline{x}_{0} + \underline{h}) = f(\underline{x}_{0}) + \left< \triangledown f(\underline{x}_{0}, \underline{h}) \right> + \frac{1}{2} \underline{h}^{T}H_{f}(\underline{x}_{0}) \underline{h} +\sigma(||\underline{h}||^{2})
$$
### Forma quadratica

Sia $f\in \mathcal C^{2}(A)$. Chiamiamo forma quadratica indotta dalla matrice Hessiana la funzione $q:\mathbb{R}^{2}\to \mathbb{R}$ definita da 
$$
q(h_{1},h_{2}) = (h_{1}, h_{2}) H_{f}(\underline{x}_{0}) \left( \begin{matrix}
h_{1} \\
h_{2}
\end{matrix} \right) 
$$

>[!tip]
>Tutte queste cose possono essere generalizzate a $n>2$ con le stesse implicazioni e proprietà

### Punto stazionario

Sia $A\subseteq \mathbb{R}^{2}$ aperto e $f: A\to \mathbb{R}$ derivabile in $(x_{0},y_{0})\in A$. Diciamo che $(x_{0},y_{0})$ è un punto stazionario o critico se 
$$
\triangledown f(x_{0},y_{0}) = 0
$$

>[!note]
>La forma di Taylor al secondo ordine diventa
>$$
>f(\underline{x}_{0} + \underline{h}) - f(\underline{x}_{0}) = \frac{1}{2} q(\underline{h}) +  \sigma(||\underline{h}||^{2})
>$$

Sia $A\subseteq \mathbb{R}^{2}$ non necessariamente aperto e $f: A\to \mathbb{R}$. Sia inoltre $(x_{0},y_{0})\in A$ allora si dice:
- punto di massimo/minimo locale o relativo di $f$ se esiste $\delta>0$ tale che $f(x_{0},y_{0})\geq f(x,y)$ $\forall {(x,y)}\in   {}B_{\delta}(x_{0},y_{0})\cap A$
- punto di massimo/minimo assoluto o globale di $f$ se $f(x_{0},y_{0})\geq f(x,y)$ $\forall {(x,y)\in} A {}$

### Punti estremali

Se $(x_{0},y_{0})$ è un punto di massimo o minimo locale allora è detto punto estremale di $f$. Inoltre se è un punto critico di $f$ che non è estremante allora si dice punto di sella di $f$

### Ottimizzazione libera

Si parla di ottimizzazione libera quando si cercano i punto estremali di $f$ nel suo dominio

### Teorema di Weierstrass

Sia $A\subseteq \mathbb R^n$ insieme chiuso e limitato e sia $f:A\to \mathbb{R}$ continua. Allora $f$ ammette massimo e minimo assoluti in $A$ quindi esistono
$$
f(\underline{x}_{m})\leq f(\underline{x})\leq f(\underline{x}_{M})
$$

### Teorema degli zeri

Sia $A$ un insieme connesso per archi in $\mathbb R^n$ e $f:A\to \mathbb{R}$ continua. Se $f(\underline{x})>0$ e $f(\underline{y})<0$ per due punti $\underline{x}$ e $\underline{y}$ in $A$, allora $\exists {\underline{z}} \in {A}$ tale che $f(\underline{z}) = 0$

### Teorema di Fermat

Sia $A\subseteq \mathbb{R}^{2}$ un insieme aperto e sia $f:A\to \mathbb{R}$ derivabile in $(x_{0},y_{0})\in A$. Se esso è un punto estremale di $f$ allora
$$
\triangledown f(x_{0},y_{0}) = 0
$$

>[!warning]
>Fermat non si applica sul bordo

### ==> [[Classificazione dei punti critici]]

### Ottimizzazione vincolata

Si parla di ottimizzazione vincolata di $f$ con vincolo $z$ per indicare la ricerca dei punti estremali di $f$ vincolati a $z$

Sia $A\subseteq \mathbb{R}^{2}$ aperto e $f,F\in\mathcal C'(A)$. Sia $z$ l'insieme di livello $0$ che viene chiamato vincolo dell'ottimizzazione.
Sia $(x_{0},y_{0})\in z$ abbiamo che
1) $\underline{x}_{0}$ è punto di massimo/minimo locale di $f$ vincolato a $z$ se esiste $\delta>0$ tale che $f(x_{0},y_{0})\geq f(x,y), \forall {(x,y)\in B_{\delta}}(x_{0},y_{0})\cap z  {}$
2) $\underline{x}_{0}$ è punto di massimo/minimo assoluto di $f$ vincolato a $z$ se $f(x_{0},y_{0})\geq f(x,y), \forall {(x,y)} \in {z}$ 
3) $\underline{x}_{0}$ è punto estremale vincolato a $z$ se è punto di massimo o minimo locale vincolato a $z$

Considero 2 strategie:
- Per sostituzione
- Moltiplicatori di Lagrange

### Strategia per sostituzione

1) Considero la funzione $g$ definita di una variabile ottenuta restringendo $f$ a $z$
	1) Esprimo il vincolo come curva dipendente da una delle due coordinate
	2) Definisco $g(x)=f(x,h(x))$ o con la $y$
2) Studio $g$ come funzione di $1$ variabile nel suo dominio e trovo i punti estremanti
3) Considero tutti i punti $(x_{0},h(x_{0}))$ dove $x_{0}$ è stato trovato al punto 2)

### Metodo dei moltiplicatori di Lagrange

Sia $A\subseteq \mathbb{R}^{2}$ aperto e siano $f,F\in\mathcal C'(A)$. Inoltre sia $(x_{0},y_{0})\in A$ un punto di estremo di $f$ vincolato sul vincolo $z = \{ (x,y)\in A : F(x,y) =0\}$. Se $\triangledown F(x_{0},y_{0}) \neq 0$, allora esiste $\lambda_{0}\in \mathbb{R}$ detto moltiplicatore di Lagrange tale che
$$
\triangledown f(x_{0},y_{0}) = \lambda_{0} \triangledown F(x_{0},y_{0})
$$
Il Teorema ci fornisce una condizione necessaria ad essere punto estremale vincolato. Possiamo vedere questo teorema coma la versione del teorema di Fermat per l'ottimizzazione vincolata. Infatti ci dice che:
- se $\lambda_{0}=0$ e $\underline{x}$ è estremale vincolato a $z$ allora sarà punto critico di $f$ appartenente a $z$
- se $\lambda_{0}\neq 0$  e $\underline{x}$ è punto estremale vincolato a $z$ allora $\triangledown f(\underline{x}) // \triangledown F(\underline{x})$

Possiamo riscrivere la condizione necessaria con il fatto che $\underline{x}$ è nel vincolo come un sistema non lineare nelle tre incognite
$$
\begin{cases}
f_{x}(\underline{x}) = \lambda_{0}F_{x}(\underline{x}) \\
f_{y}(\underline{x}) = \lambda_{0}F_{y}(\underline{x}) \\
F(\underline{x} )= 0
\end{cases}
$$
che viene spesso riscritto come
$$
\triangledown L(\underline{x},\lambda_{0}) = 0
$$
dove $L_\lambda$ è una funzione in 3 variabili detta Lagrangiana e definita da
$$
L(x,y,z) = f(x,y) - zF(x,y)
$$

### Vincoli con diseguaglianza nel caso di un insieme non unidimensionale chiuso e limitato

Sia $f:A\subseteq \mathbb R^n\to \mathbb{R}$ continua definita su $A$ chiuso e limitato.

1) $A$ è chiuso e limitato, $f$ è continua. Quindi per Weierstrass esistono massimi e minimi in $A$
2) Escludo momentaneamente il bordo di $A$ e usando il teorema di Fermat su $Int(A)$ applico l'ottimizzazione libera ($P,Q$)
3) Cerco i punti candidati sul bordo di $A$ come punti estremali di $f$ vincolati al vincolo $z=$ bordo di $A$ utilizzando l'ottimizzazione vincolata $(R)$
4) Confronto i valori delle immagini
$$
\begin{align}
max_{\underline{x}\in A}f(\underline{x}) = max \{ f(P_{1}),\dots,f(P_{k}),f(Q_{1}),\dots,f(Q_{k}),f(R_{1}),\dots,f(R_{k}) \} \\
max_{\underline{x}\in A}f(\underline{x}) = min \{ f(P_{1}),\dots,f(P_{k}),f(Q_{1}),\dots,f(Q_{k}),f(R_{1}),\dots,f(R_{k}) \}
\end{align}
$$
