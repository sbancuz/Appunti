---
tags: [analisi_1]
---
Ogni successione definitivamente monotona è regolare
1. $\{{a_{n}}\}_{n\in N}$ è crescente e superiormente limitata, allora converge per difetto
2. se $\{{a_{n}}\}_{n\in N}$ è crescente e illimitata, allora diverge a $+\infty$
3. se $\{{a_{n}}\}_{n\in N}$ è decrescente e inferiormente limitata, allora converge per eccesso
4. se $\{{a_{n}}\}_{n\in N}$ è decrescente e illimitata, allora diverge a $-\infty$

>[!note]- Dimostrazione
>Sia $\{{a_{n}}\}_{n\in N}$ crescente e limitata superiormente, allora per l'[[assioma di dedekind]], l'[[insieme]] $\{a_{n}\text{ | } n\in N\}$ ha estremo superiore, sia questo estremo $l$ .
>Per definizione di sup, abbiamo che $\forall {\epsilon} \gt {0}$ esiste un elemento di  $\{a_{n}\text{ | } n\in N\}$, cioè un certo $a_{m}$ tale che $l-\epsilon\lt a_{m}$.
>Ma la successione $\{{a_{n}}\}_{n\in N}$ è crescente quindi $\forall {n} \ge {m}$, si ha $l-\epsilon\le a_{m}\le a_{n}\le l$


Sia  $a=\{a_n\}_{n\in N}$, si dice che $a$ diverge a +inf se 
```math
||{"id":540833062144}||

\forall M\gt 0, \exists n_0\in N, \forall n\ge 0 \text{ si ha } a_n \gt M
```

Sia  $a=\{a_n\}_{n\in N}$, si dice REGOLARE se è divergente o convergente, sarà IRREGOLARE se no.


![[Algebra dei limiti]]

![[Gerarchia degli infiniti]]

![[Permanenza del segno per successioni monotone]]

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

![[Teorema di monotonia delle successioni convergenti]]

![[Teorema del confronto per le successioni monotone]]

## Criterio di convergenza per le successioni monotone
Ogni successioni definitivamente monotona è regolare
1. $\{{a_{n}}\}_{n\in N}$ è crescente e superiormente limitata, allora converge per difetto
2. se $\{{a_{n}}\}_{n\in N}$ è crescente e illimitata, allora diverge a $+\infty$
3. se $\{{a_{n}}\}_{n\in N}$ è decrescente e inferiormente limitata, allora converge per eccesso
4. se $\{{a_{n}}\}_{n\in N}$ è decrescente e illimitata, allora diverge a $-\infty$

>[!note]- Dimostrazione
>Sia $\{{a_{n}}\}_{n\in N}$ crescente e limitata superiormente, allora per l'[[assioma di dedekind]], l'[[insieme]] $\{a_{n}\text{ | } n\in N\}$ ha estremo superiore, sia questo estremo $l$ .
>Per definizione di sup, abbiamo che $\forall {\epsilon} \gt {0}$ esiste un elemento di  $\{a_{n}\text{ | } n\in N\}$, cioè un certo $a_{m}$ tale che $l-\epsilon\lt a_{m}$.
>Ma la successione $\{{a_{n}}\}_{n\in N}$ è crescente quindi $\forall {n} \ge {m}$, si ha $l-\epsilon\le a_{m}\le a_{n}\le l$
