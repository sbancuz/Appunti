---
tags: [analisi_2]
---
L'obiettivo delle EDO è di trovare una funzione $y$ derivabile con derivata $y'$

>[!note] Esempio
>$$
> y'(t) = \frac{1}{t} \implies 
> \begin{cases}
> y = \log(t) + c_{1}& \forall {t} > {0}  \\
>  y = \log(-t) + c_{2}& \forall {t} < {0}
>\end{cases}
> 
>$$
>dove $y$ è una funzione incognita.
>
>Per $t = 0$,  $y'$ non è definita quindi non c'è una funzione derivale.

La soluzione di una EDO dipende quindi anche dall'intervallo su cui è definita, e può essere diverso dall'intervallo su cui è definita.

Per passare al caso generale serve il concetto di [[Funzioni a più variabili]]

Una EDO di ordine $n\in \mathbb N$ è una equazione che ha  come incognita una funzione $y(t)$ che coinvolge la derivata n-esima di $y$ e può coinvolgere le derivate y-esime con $1\leq y\leq n-1$ cioè si può scrivere nella forma
$$
F(t,y(t),y'(t),t''(t),\dots,y^{(k)}(t)) = 0, t \in I
$$
dove $I$ è un intervallo in $\mathbb R$ e $F$ è una funzione in n-variabili. Inoltre si chiama soluzione particolare della EDO in un intervallo $J \subset I$ ogni funzione $\overline{y}(t)\in \mathcal C^{n}(J)$. L'[[insieme]] di tutte le soluzioni si chiama integrale generale.

### Ordine di una EDO

L'ordine di una EDO è dato dal più grande grado di derivazione presente in un equazione. L'esempio sopra è di grado $1$.

### Forma normale

Si dice che una EDO di ordine n è in forma normale se esiste $f:\mathbb R^{n+1} \to \mathbb R$ tale che si può scrivere nella forma
$$
y^{(n)} = f(t,y(t),y'(t),t''(t),\dots,y^{(n-1)}(t)), t \in I
$$

>[!note] Esempio
>$$
>y'(t) = t \sqrt{ y^{2}(t) + 1 } \implies f(t,s ) = t \sqrt{ s^{2}  + 1}
>$$

### Risoluzione => [[Problema di Cauchy]]

### Tipologie di EDO
 - [[EDO A variabili separabili]]
 -  [[EDO Lineari]]