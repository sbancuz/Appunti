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

