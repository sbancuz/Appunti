(size - j - 1)-thOgni successioni definitivamente monotona è regolare
1. $\{{a_{n}}\}_{n\in N}$ è crescente e superiormente limitata, allora converge per difetto
2. se $\{{a_{n}}\}_{n\in N}$ è crescente e illimitata, allora diverge a $+\infty$
3. se $\{{a_{n}}\}_{n\in N}$ è decrescente e inferiormente limitata, allora converge per eccesso
4. se $\{{a_{n}}\}_{n\in N}$ è decrescente e illimitata, allora diverge a $-\infty$

>[!note]- Dimostrazione
>Sia $\{{a_{n}}\}_{n\in N}$ crescente e limitata superiormente, allora per l'[[assioma di dedekind]], l'insieme $\{a_{n}\text{ | } n\in N\}$ ha estremo superiore, sia questo estremo $l$ .
>Per definizione di sup, abbiamo che $\forall {\epsilon} \gt {0}$ esiste un elemento di  $\{a_{n}\text{ | } n\in N\}$, cioè un certo $a_{m}$ tale che $l-\epsilon\lt a_{m}$.
>Ma la successione $\{{a_{n}}\}_{n\in N}$ è crescente quindi $\forall {n} \ge {m}$, si ha $l-\epsilon\le a_{m}\le a_{n}\le l$


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
>Sia $a=\{{a_{n}}\}_{n\in N}$ convergente, $\lim_{ n \to \infty } {a_{n}}=l$ e sia $\{{a_{n}}\}_{n\in N}$ definitivamente $\ge 0$ allora $l\ge 0$
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

>[!info] Teorema di monotonia
>Siano $\{{a_{n}}\}_{n\in N}$ e $\{{b_{n}}\}_{n\in N}$ siccessioni convergenti tali che $\lim_{ n \to \infty } {a_{n}} = l$ e $\lim_{ n \to \infty } {b_{n}}=l_{1}$
>Se definitivamente $a_{n}\le b_{n}$ allora $l\le l_{1}$
>>[!note]- Dimostrazione
>>Sia $\{{c_{n}}\}_{n\in N}$ la successione $c_{n}=b_{n}-a_{n}$ allora $\{{c_{n}}\}_{n\in N}$ converge a $l_{1}-l$, e $\{{c_{n}}\}_{n\in N}$ è definitivamente positiva, quindi per la permanenza del segno $l_{1}-l\ge 0$

>[!info] Teorema del confronto
>Siano $\{{a_{n}}\}_{n\in N}$, $\{{b_{n}}\}_{n\in N}$, $\{{c_{n}}\}_{n\in N}$ successioni convergenti rispettivamente a $l,l_{1},l_{2}$.
>Se definitivamente $a_{n}\le b_{n}\le c_{n}$ allora $l\le l_{1}\le l_{2}$

>[!warning]
>Se   $a_{n}\lt b_{n}\lt c_{n}$ allora posso solo dire $l\le l_{1}\le l_{2}$
>

## Criterio di convergenza per le successioni monotone
Ogni successioni definitivamente monotona è regolare
1. $\{{a_{n}}\}_{n\in N}$ è crescente e superiormente limitata, allora converge per difetto
2. se $\{{a_{n}}\}_{n\in N}$ è crescente e illimitata, allora diverge a $+\infty$
3. se $\{{a_{n}}\}_{n\in N}$ è decrescente e inferiormente limitata, allora converge per eccesso
4. se $\{{a_{n}}\}_{n\in N}$ è decrescente e illimitata, allora diverge a $-\infty$

>[!note]- Dimostrazione
>Sia $\{{a_{n}}\}_{n\in N}$ crescente e limitata superiormente, allora per l'[[assioma di dedekind]], l'insieme $\{a_{n}\text{ | } n\in N\}$ ha estremo superiore, sia questo estremo $l$ .
>Per definizione di sup, abbiamo che $\forall {\epsilon} \gt {0}$ esiste un elemento di  $\{a_{n}\text{ | } n\in N\}$, cioè un certo $a_{m}$ tale che $l-\epsilon\lt a_{m}$.
>Ma la successione $\{{a_{n}}\}_{n\in N}$ è crescente quindi $\forall {n} \ge {m}$, si ha $l-\epsilon\le a_{m}\le a_{n}\le l$



## Criterio di convergenza per le successioni monotone
Ogni successioni definitivamente monotona è regolare
1. $\{{a_{n}}\}_{n\in N}$ è crescente e superiormente limitata, allora converge per difetto
2. se $\{{a_{n}}\}_{n\in N}$ è crescente e illimitata, allora diverge a $+\infty$
3. se $\{{a_{n}}\}_{n\in N}$ è decrescente e inferiormente limitata, allora converge per eccesso
4. se $\{{a_{n}}\}_{n\in N}$ è decrescente e illimitata, allora diverge a $-\infty$

>[!note]- Dimostrazione
>Sia $\{{a_{n}}\}_{n\in N}$ crescente e limitata superiormente, allora per l'[[assioma di dedekind]], l'insieme $\{a_{n}\text{ | } n\in N\}$ ha estremo superiore, sia questo estremo $l$ .
>Per definizione di sup, abbiamo che $\forall {\epsilon} \gt {0}$ esiste un elemento di  $\{a_{n}\text{ | } n\in N\}$, cioè un certo $a_{m}$ tale che $l-\epsilon\lt a_{m}$.
>Ma la successione $\{{a_{n}}\}_{n\in N}$ è crescente quindi $\forall {n} \ge {m}$, si ha $l-\epsilon\le a_{m}\le a_{n}\le l$

