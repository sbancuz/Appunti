---
tags: [analisi 1]
---
Una successione $a=\{a_n\}_{n\in N}$ si dice CONVERGENTE se esiste un numero reale $l\in R$ tale che per ogni $\epsilon \gt 0$ definitivamente si ha $|a_n - l | \le \epsilon$ 
```math
||{"id":747507161468}||


```
Si dice che l'intervallo $[l-\epsilon,l+\epsilon]$ è un intorno circolare centrato in $l$ di raggio $\epsilon$
Se è $a_n$ è convergente allora si dice che $a_n$ converge ad $l$ 
$$
	\lim_{n\to \inf} a_n = l
$$ 
sia $a=\{a_n\}_{n\ge 0}$ una successione convergente, allora $a$ converge ad un unico limite.

>[!note]- Dimostrazione
>Siano $l_1,l_2$ 2 limiti per $a$, allora 
>
>$\forall\epsilon\gt0 \exists n_1,n_2\in N \text{ | } \forall n\ge n_1$ si ha $|a_n - l_1|\le \epsilon$ e $\forall n\ge n_2$ si ha $|a_n - l_2|\le \epsilon$
>
>ovvero $\exists n_0 = max\{n_1,n_2\}$ tc $\forall n\ge n_0$ si ha $|a_n - l_1|\le \epsilon$ e $|a_n - l_2|\le \epsilon$ allora si ha che $|l_1-l_2| \le 2\epsilon$
>
>Se per assurdo $l_1\not=l_2$ allora $|l_1-l_2|=k\gt 0$, ma se prendo $\epsilon = k/3$ avrò $k\le {2k}/3$ che è assurdo 

Ogni successione convergente è limitata

>[!note]- Dimostrazione
Sia $a=\{a_n\}_{n\in N}$ e sia $\lim_{n\to \inf} a_n = l$ posso prendere $\epsilon=1$, $\exists n_0\in N\text{ | } \forall n\ge n_0$ si ha $|a_n-l| \le 1$ cioè $l-1\le a_n\le l+1$ quindi a è definitivamente limitata.
D'altra parte l'insieme $\{a_0,a_1,...,a_n\}$ è finito quindi ha massimo M e minimo m, dunque $\forall n\in N, a_n \le max\{M,l+1\} \text{ e } a_n \ge min\{m,l-1\}$ e perciò a è limitata

 ![[Criterio di convergenza per le successioni monotone]]