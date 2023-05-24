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