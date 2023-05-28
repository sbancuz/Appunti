---
tags: analisi_2
---

Consideriamo un punto 
$$
\underline{x} = \left( \begin{matrix}
x_{1}\\x_{2}\\x_{3}
\end{matrix} \right) \in \mathbb R^{3} 
$$
e lo spostiamo nello spazio tracciando la sua traiettoria nel tempo. Questo equivale a tracciare una curva nello spazio.

### Curva in $\mathbb R^n$ con sostegno $\gamma$ è definita in forma parametrica da n funzioni

Siano
$$
r_{1},r_{2},\dots,r_{n}: I\subseteq \mathbb R\to \mathbb R
$$
dove $I \subseteq \mathbb R$ è un intervallo chiuso che si può scrivere come funzione vettoriale
$$
\underline{r}(t) = \left( \begin{matrix}
r_{1}(t)\\r_{2}(t)\\ \vdots \\ r_{n}(t)
\end{matrix} \right) = \sum_{i}^{n}r_{i}(t)\underline{e}_{i}
$$
In particolare ci riferiamo a $\underline{r}(t)$ anche come la parametrizzazione della curva e a
$$
\gamma = \underline{r}(I) = \{ (x_{1},\dots,x_{n})\in \mathbb R^n : \exists {t} \in {I} \text{ con } r_{i}(t)=x_{i}  \}
$$
come al sostegno della curva.

>[!note]
>Due curve con lo stesso sostegno sono dette equivalenti

### Curva chiusa/semplice

Diciamo che $\underline{r}:[a,b]\to \mathbb R^n$ è
- chiusa se $\underline{r}(a)=\underline{r}(b)$
- semplice se $\underline{r}$ è ristretta all'intervallo aperto $(a,b)$

### Limiti

Hanno le stesse proprietà dei [[Limiti di funzioni a 1 variabile]]

Sia $\underline{r}:I\subseteq \mathbb R \to \mathbb R^n$ una curva in un intervallo I allora
$$
\exists {\lim_{ t \to t_{0} } {\underline{r}(t)}} = \underline{r}^{0}\in \mathbb R^n
$$
### Classe

Sia $\underline{f}$ una curva definita sui numeri reali, allora si dice di classe $\mathcal C^{\alpha}$ se $f_{i}\in\mathcal C^{\alpha}$

### Curva regolare

Sia $\underline{r}$ una curva reale definita su $I$, i bordi dell'intervallo non contano per questa definizione. Diciamo che è regolare se
- $\underline{r}\in\mathcal C^{1}$
- $\underline{r}'(t)\neq \underline{0}$

>[!tip]
>Si può anche definire come la [[norma]] della derivata diversa da 0

Si può pero dire che una curva è regolare a tratti se :
- $\underline{r}\in\mathcal C^{1}$
- $\underline{r}'(t)\neq \underline{0}$ ad eccezione di un numero definito di punti

### Sostegno parametrizzabile come grafico

Un sostegno $\gamma$ si dice parametrizzabile come grafico di una funzione $f$ se $\exists {f} \in {\mathcal C}$ tale che $\gamma$ è il sostegno della curva definita da $\underline{r}: I\subseteq \mathbb R\to \mathbb R^{2}$ con
$$
\begin{cases}
r_{1}(t) =t  \\
r_{2}(t) = f(t)
\end{cases}
$$
>[!nota]
>Se la $f\in\mathcal C^{1}$ allora sarà parametrizzabile come grafico


### [[Versori]] tangente

Sia $\underline{r}: I\subseteq \mathbb R\to \mathbb R^{n}$ una curva regolare. Chiamiamo versore tangente a $\underline{r}$ il versore
$$
\underline{T}(t) = \frac{\underline{r}'(t)}{|| \underline{r}'(t)||}
$$

### Lunghezza di una curva

Sia $\underline{r}: I\subseteq \mathbb R\to \mathbb R^n$ una curva regolare su un intervallo $I$ con sostegno $\gamma$. Si dice lunghezza di $\gamma$ il numero
$$
L(\gamma) = \int _{I}| | \underline{r}'(t) | | \, dt 
$$
#### Lunghezza per regolare a tratti

Sia $I$ un intervallo in $\mathbb R$ con estremi $a,b \in \mathbb R \cup\{\pm \infty\}$ e sia $\underline{r} : I\to \mathbb R^n$ una curva regolare a tratti con sostegno $\gamma$. Si dice lunghezza
$$
L(\gamma) = \int _{a}^{t_{1}}| | \underline{r}'(t) | | \, dt  + \int _{t_{1}}^{t_{2}}| | \underline{r}'(t) | | \, dt +\dots+\int _{t_{k}}^{t_{b}}| | \underline{r}'(t) | | \, dt
$$

### Riparametrizzazione di $\gamma$

Siano $I$ e $J$ due intervalli in $\mathbb R$. Sia $\underline{r}:I \to \mathbb R^n$ una curva con sostegno $\gamma$ e si a $\phi:J\to I$ una funzione derivabile in $J$ e invertibile.
Si chiama riparametrizzazione di $\gamma$ la nuova curva $\underline{v}:J\to \mathbb R^n$ definita da
$$
\underline{v}(s)= \underline{r} \cdot \phi (s) = \underline{r}(\phi(s))
$$
>[!note] 
>$\phi:J\to I$ derivabile in Int$J$ e invertibile implica che $\phi$ è monotona. cioè o strettamente crescente o strettamente descrescente 

### Teorema di invarianza della lunghezza di una curva per riparametrizzazioni

Sia $\underline{r}:[a,b] \subseteq \mathbb R \to \mathbb R^n$ una curva regolare di sostegno $\gamma$ e sia $\underline{v}: [c,d] \subseteq \mathbb R \to \mathbb R^n$ una riparametrizzazione di $\gamma$ relativa al cambiamento di variabile $\phi:[c,d] \to [a,b]$. Abbiamo che 
$$
L(\underline{r}([a,b])) = \int _{c}^{d} | | v'(s)| |  \, ds = \int _{a} ^{b} | | \underline{r}'(t)| |  \, dt 
$$

#### Dimostrazione

Ricordiamo che siccome $\underline{r}$ è regolare, abbiamo che $L(\underline{r}([a,b])) =\int _{a} ^{b} | | \underline{r}'(t)| |  \, dt$.
Unendo la formula di derivazione di funzione composte componente per componente otteniamo $\forall {s} \in {(c,d)}$
$$
\underline{v}'(s) = (\underline{r}(\phi(s)))' = \underline{r}'(\phi(s))\phi'(s)
$$
e quindi,
$$
|| \underline{v}'(s) | | = | \phi'(s) | \cdot | | \underline{r}'(\phi(s))| |
$$
Vogliamo fare il cambio di variabile $t=\phi(s)$ che implica $dt = \phi'(s)ds$ e per gli estremi di integrazione abbiamo due possibilità:
- Se $\phi$ è crescente allora $\phi(c) = a<b=\phi(d), \phi'(s)\geq 0$ $\forall {s} \in {(c,d)}$ e $|| \underline{v}'(s) | | =  \phi'(s)  \cdot | | \underline{r}'(\phi(s))| |$
- Se $\phi$ è decrescente allora $\phi(c) = b<a=\phi(d), \phi'(s)\leq 0$ $\forall {s} \in {(c,d)}$ e $|| \underline{v}'(s) | | =  -\phi'(s)  \cdot | | \underline{r}'(\phi(s))| |$

Nel primo caso abbiamo che
$$
\int _{a}^{b} | | \underline{r}'(t) | | dt \, = \int _{c} ^d  \underline{r}'(\phi(s))\phi'(s)\, ds  = \int _{c} ^d  || \underline{v}'(s)| | \, ds   
$$
Nel secondo caso
$$
\int _{a}^{b} | | \underline{r}'(t) | | dt \, = \int _{d} ^c  \underline{r}'(\phi(s))(-\phi'(s))\, ds  = \int _{c} ^d  \underline{r}'(\phi(s))\phi'(s)\, ds = \int _{c} ^d  || \underline{v}'(s)| | \, ds   
$$

### Lunghezza d'arco

Se $\underline{r}:[a,b] \to \mathbb R^n$ è una curva con sostegno $\gamma$, la lunghezza f'arco di $\underline{r}$ da $a$ a $t\in[a,b]$ è una funzione di $t$ definita da
$$
s(t) = \int _{a} ^{t }||\underline{r}'(\tau) \, d\tau 
$$
mentre la lunghezza dell'arco elementare, quando calcolabile, è la quantità 
$$
ds = ||\underline{r}'(t)|| dt
$$
Inoltre, se la funzione lunghezza d'arco esiste, è derivabile ed è invertibile. Allora chiamiamo $s$ parametro d'arco o ascissa curvilinea di $\gamma$, e possiamo riparametrizzare $\gamma$ rispetto al parametro d'arco di variabile $s^{-1}$ cioè
$$
\underline{v}(s) = \underline{r}(s^{-1}(s))
$$