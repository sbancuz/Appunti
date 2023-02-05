Si chiama successione una qualunque funzione da $N\to R$ o più generalmente da un sottoinsieme di $N$ del tipo $\{n\in N \text{ | }n\ge c\}$ in $R$ dove $c$ è una costante arbitraria.

Se ho $f:N\to R$, $f$ è una successione e la rappresento $f_n$ e più in generale si indica $$
f=\{f_n\}_{n\in N}
$$
>[!tip] Esempio
>se $a=\{n^2\}_{n\in }N$ allora $a_5=25$

Una successione è un particolare tipo di [[Funzioni]]. 

Sia $a=\{a_n\}_{n\in N}$ una successione e sia $P$ una proprietà che abbia senso per le successione si dice che $a$ possiede la propietà $p$ DEFINITIVAMENTE
se $\exists n_0\in N$ tc la successione $\overline{a}=\{a_n\}_{n\ge n_0}$

## Convergenza

Una successione $a={a_n}_{n\in N}$ si dice CONVERGENTE se esiste un numero reale $l\in R$ tale che per ogni $\epsilon \gt 0$ definitivamente si ha $|a_n - l | \le \epsilon$ 
```math
||{"id":747507161468}||


```
Si dice che l'intervallo $[l-\epsilon,l+\epsilon]$ è un intorno circolare centrato in $l$ di raggio $\epsilon$
Se è $a_n$ è convergente allora si dice che $a_n$ converge ad $l$ $$
	\lim_{n\to \inf} a_n = l
$$ 
>[!info] Teorema dell'unicità del limite
>sia $a=\{a_n\}_{n\ge 0}$ una successione convergente, allora $a$ converge ad un unico limite.
>>[!note]- Dimostrazione
>>Siano $l_1,l_2$ 2 limiti per $a$, allora 
>>
>>$\forall\epsilon\gt0 \exists n_1,n_2\in N \text{ | } \forall n\ge n_1$ si ha $|a_n - l_1|\le \epsilon$ e $\forall n\ge n_2$ si ha $|a_n - l_2|\le \epsilon$
>>
>>ovvero $\exists n_0 = max\{n_1,n_2\}$ tc $\forall n\ge n_0$ si ha $|a_n - l_1|\le \epsilon$ e $|a_n - l_2|\le \epsilon$ allora si ha che $|l_1-l_2| \le 2\epsilon$
>>
>>Se per assurdo $l_1\not=l_2$ allora $|l_1-l_2|=k\gt 0$, ma se prendo $\epsilon = k/3$ avrò $k\le {2k}/3$ che è assurdo 

