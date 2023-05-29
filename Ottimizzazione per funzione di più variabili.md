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

Si parla di ottimizzazione libera quando si cercano i punto estremali di $f$nel suo dominio