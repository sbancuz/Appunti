---
tags: analisi_2
---
Una EDO del secondo ordine lineare è un equazione della forma:
$$
a(t)y''(y)+b(t)y'(t)+c(t)y(t)=f(t)
$$
dove $a,b,c,d:I\subseteq \mathbb R\to \mathbb R$ e $a\neq 0$, nell'incognita $y:J\subseteq I\to \mathbb R$. Nel caso $f=0$ si parla di EDO omogenea se no completa.

### Integrale generale

L'integrale generale della EDO del secondo ordine è la famiglia di tutte le soluzioni dell'equazione in questione.

### [[Problema di Cauchy]]

### Teorema di esistenza e unicità globale per il problema di Cauchy

Dato il problema di Cauchy 
$$
\begin{cases}
a(t)y''(y)+b(t)y'(t)+c(t)y(t)=f(t) \\
y(t_{0}) = y_{0} \\
y'(t_{0}) = z_{0}
\end{cases}
$$
dove $a,b,c,d:I\subseteq \mathbb R\to \mathbb R$ continue e $a\neq 0$, e assegnati $t_{0}\in I$ e $y_{0},z_{0}\in \mathbb R$. Esso ammette un'unica soluzione $y(t) ,\forall {t\in I}  {}$

>[!note]
>Il teorema ci dice 3 cose importanti
>1) esiste una soluzione $y:J\subseteq I\to \mathbb R$
>2) la soluzione è unica
>3) $J=I$

### [[Principio di sovrapposizione]]

### Struttura dell'integrale generale delle EDO del secondo ordine lineare

Siano $a,b,c:I\subset \mathbb R\to \mathbb R$ continue con $a\neq 0$.

L'integrale generale dell'equazione omogenea è
$$
a(t)y''(y)+b(t)y'(t)+c(t)y(t)=0
$$
ed è uno [[Spazio vettoriale]] di dimensione 2, cioè le soluzioni sono tutte della forma
$$
y_{\sigma}(t) = c_{1}y_{\sigma,1}(t)+c_{2}y_{\sigma,2}(t)
$$
con $c_{1},c_{2}\in \mathbb R$, dove $y_{\sigma,1}$ e$y_{\sigma,2}$ sono le 2 soluzioni linearmente indipendenti

#### Dimostrazione


