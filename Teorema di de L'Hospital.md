---
tags: [analisi 1]
---
Siano $f,g:(a,b)\to R$ continue e derivabili in $(a,b)$ e siano poi $g$ e $g'$ non nulle in $(a,b)$.
Se:
	1. $\lim_{ x \to a^+ } {f(x)}=\lim_{ x \to a^+ } {g(x)}=0$ oppure sono $\infty$ o $-\infty$
	2. $\lim_{ x \to a^+ } \frac{{f'(x)}}{g'(x)}=l\in R\cup\{-\infty,\infty\}$
Allora 
$$
\lim_{ x \to a^+ } \frac{{f(x)}}{g(x)}=l
$$
Lo stesso vale per $x\to b^-$

>[!note]- Dimostrazione
>Considero solo il caso in cui $f(x_{}),g(x)\to {0}$ per $x\to a^+$
>Sia $\{{s_{n}}\}_{n\in N}$ una successione contenutta in $(a,b)$ che tenda ad $a$
>Possiamo prolungare con continuità $f$ e $g$ ponendo $f(a)=0$ e $g(a)=0$
>Allora $\forall n \in N$
>$$
\frac{f(x_{n})}{g(x_{n})}= \frac{f(x_{n})-f(a)}{g(x_{n})-g(a)}
>$$
>Definisco $h(x)=f(x_{n})g(x)-g(x_{n})f(x)=0$, in più poiché $f,g$ sono continue e derivabili in $(a,x_{n})$ anche $h$ lo sarà.
>Questo soddisfa Lagrange e quindi $h'(t_{n})=f(x_{n})g'(t_{n})-g(x_{n})f'(t_{n})=0$
>Quindi
>$$
\frac{f(x_{n})}{g(x_{n})} = \frac{f'(t_{n})}{g'(t_{n})}
>$$
>Passo al limite per $n\to \infty$
>$$
>\lim_{ x \to a^+ } \frac{{f(x)}}{g(x)}=l
>$$