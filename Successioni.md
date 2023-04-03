---
tags: [analisi_1]
---
Si chiama successione una qualunque funzione da $N\to R$ o più generalmente da un sottoinsieme di $N$ del tipo $\{n\in N \text{ | }n\ge c\}$ in $R$ dove $c$ è una costante arbitraria.

Se ho $f:N\to R$, $f$ è una successione e la rappresento $f_n$ e più in generale si indica 
$$
f=\{f_n\}_{n\in N}
$$
>[!tip] Esempio
>
>se $a=\{n^2\}_{n\in }N$ allora $a_5=25$

Una successione è un particolare tipo di [[Funzioni]]. 

Sia $a=\{a_n\}_{n\in N}$ una successione e sia $P$ una proprietà che abbia senso per le successione si dice che $a$ possiede la propietà $p$ DEFINITIVAMENTE
se $\exists n_0\in N$ tc la successione $\overline{a}=\{a_n\}_{n\ge n_0}$

![[Convergenza successioni]]

Una successione $a=\{a_n\}_{n\in N}$ si dice infinitesima se $$\lim_{n\to \inf} a_n = 0$$
Sia $a=\{a_n\}_{n\ge 0}$ una successione limitata e  $b=\{b_n\}_{n\ge 0}$ una successione infinitesima, allora $$ab = \{a_nb_n\}_{n\ge 0}$$ è una successione infinitesima

>[!note]- Dimostrazione
>$a$ è limitata -> esiste M > 0 tc $\forall n\ge0$ si ha $|a_n|\le M$
>$b_n\to 0$ per $n\to \inf$ : $\forall \epsilon \gt 0, \exists n_0 \in N$ tc $\forall n \gt n_0$ si ha $|b_n -0| \le \epsilon$
>Allora  $\forall \epsilon \gt 0, \exists n_0 \in N$ tc $\forall n \gt n_0$ si ha $|a_nb_n|\le M\epsilon$
>Ma M è costante fissata, quindi posso prendere $\epsilon \gt 0$ in omdo tale che $M\epsilon$ sia un qualunque reale positivo
