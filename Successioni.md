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

Una successione $a=\{a_n\}_{n\in N}$ si dice CONVERGENTE se esiste un numero reale $l\in R$ tale che per ogni $\epsilon \gt 0$ definitivamente si ha $|a_n - l | \le \epsilon$ 
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

>[!info] Teorema dell'unicità del limite
>
>Ogni successione convergente è limitata
>>[!note]- Dimostrazione
Sia $a=\{a_n\}_{n\in N}$ e sia $\lim_{n\to \inf} a_n = l$ posso prendere $\epsilon=1$, $\exists n_0\in N\text{ | } \forall n\ge n_0$ si ha $|a_n-l| \le 1$ cioè $l-1\le a_n\le l+1$ quindi a è definitivamente limitata.
D'altra parte l'insieme $\{a_0,a_1,...,a_n\}$ è fubuti quindi ha massimo M e minimo m, dunque $\forall n\in N, a_n \le max\{M,l+1\} \text{ e } a_n \ge min\{m,l-1\}$ e perciò a è limitata

Una successione $a=\{a_n\}_{n\in N}$ si dice infinitesima se $$\lim_{n\to \inf} a_n = 0$$
Sia $a=\{a_n\}_{n\ge 0}$ una successione limitata e  $b=\{b_n\}_{n\ge 0}$ una successione infinitesima, allora $$ab = \{a_nb_n\}_{n\ge 0}$$ è una successione infinitesima

>[!note]- Dimostrazione
>$a$ è limitata -> esiste M > 0 tc $\forall n\ge0$ si ha $|a_n|\le M$
>$b_n\to 0$ per $n\to \inf$ : $\forall \epsilon \gt 0, \exists n_0 \in N$ tc $\forall n \gt n_0$ si ha $|b_n -0| \le \epsilon$
>Allora  $\forall \epsilon \gt 0, \exists n_0 \in N$ tc $\forall n \gt n_0$ si ha $|a_nb_n|\le M\epsilon$
>Ma M è costante fissata, quindi posso prendere $\epsilon \gt 0$ in omdo tale che $M\epsilon$ sia un qualunque reale positivo

Sia  $a=\{a_n\}_{n\in N}$, si dice che $a$ diverge a +inf se 
```math
||{"id":540833062144}||

\forall M\gt 0, \exists n_0\in N, \forall n\ge 0 \text{ si ha } a_n \gt M
```

Sia  $a=\{a_n\}_{n\in N}$, si dice REGOLARE se è divergente o convergente, sarà IRREGOLARE se no.

>[!info] Teorema dell'algebra dei limiti
Siano $a=\{a_n\}_{n\in N}$, $b=\{b_n\}_{n\in N}$ convergenti e sia $\lim_{n\to \inf} a_n = l_a$, $\lim_{n\to \inf} b_n = l_b$ allora:
• $\forall \alpha,\beta\in R$ la successione $\alpha a_n + \beta b_n$ è convergente e il suo limite è $$\lim_{n\to \inf}\alpha a_n + \beta b_n=\alpha l_a + \beta l_b$$
• la successione $\{a_nb_n\}_{n\in N}$ converge a $$\lim_{n\to \inf}a_nb_n=l_a l_b$$
• se $\forall n \in N$ si ha $b_{n} \not= 0$ e $l_{b}\not=0$ allora anche la successione $\{\frac{a_{n}}{b_{n}}\}_{n\in N}$ converge e $\lim_{ n \to \infty }\frac{a_{n}}{b_{n}}=\frac{l_{a}}{l_{b}}$ 
• se $\forall n \in N$ si ha $a_{n}\gt 0$ e $l\gt 0$ allora anche la successione $\{{a_{n}^{b_{n}}}\}_{n\in N}$ converge e $\lim_{ n \to \infty }{a_{n}^{b_{n}}} = l_{a}^{l_{b}}$

>[!warning]
>I risultati qui sopra valgono se $\{{a_{n}}\}_{n\in N}$ e $\{{b_{n}}\}_{n\in N}$ sono convergenti

>[!info] Teorema della gerarchia degli infiniti
>Per ogni $a\gt 1$ e $\alpha\gt{0}$ si ha:
>• $\lim_{ n \to \infty }{\frac{\log_{a}n}{n^\alpha}} = 0$
>• $\lim_{ n \to \infty }{\frac{n^\alpha}{a^n}}$

>[!info] Teorema di permanenza del segno
>Sia $a=\{{a_{n}}\}_{n\in N}$ convergente tc definitivamente si abbia $a_{n}\ge {0}$ allora $\lim_{ n \to \infty } {a_{n}}\ge 0$
>>[!note]- Dimostrazione
>> Sia $l=\lim_{ n \to \infty } {a_{n}}$, allora $\forall\epsilon\gt 0 ,\exists n \in N ,\forall {n} \ge {n_{0}}$ si ha $|a_{n}-l|\le\epsilon$, inoltre posso scegliere $n_{0}$ in modo tale che $a_{n}\ge 0$
>> Quindi abbiamo che $\forall {\epsilon} \ge {0},\forall {n} \ge {n_{0}}$ si ha $0\le a_{n}\le l+\epsilon$
>> Ora, se $l$ fosse $< 0$, potrei prendere $\epsilon$ compresa tra 0 e $-l$ e avrei che $l+\epsilon \lt 0$ da cui $0\le a_{n} \le l+\epsilon\le 0$ che è un assurdo, quindi $l\ge 0$
>> 

Sia $\{{a_{n}}\}_{n\in N}$ una successione convergente con limite $l$, se $\forall {\epsilon} \gt {0},\exists n_{0} \in N,\forall {n} \ge {n_{0}}$ si ha $l\le a_{n}\le l+\epsilon$ e si dice che $\{{a_{n}}\}_{n\in N}$ tende a $l$ per ECCESSO e si scrive $$
\lim_{ n \to \infty } {a_{n}}=l^+
$$
```math
||{"id":585169041992}||


```
Analogamente sia $\{{a_{n}}\}_{n\in N}$ una successione convergente con limite $l$, se $\forall {\epsilon} \gt {0},\exists n_{0} \in N,\forall {n} \ge {n_{0}}$ si ha $l-\epsilon\le a_{n}\le l$ e si dice che $\{{a_{n}}\}_{n\in N}$ tende a $l$ per DIFETTO e si scrive $$
\lim_{ n \to \infty } {a_{n}}=l^-
$$
>[!warning]
>Ci sono successioni convergenti che non tendono al loro limite nè per eccesso nè per difetto

