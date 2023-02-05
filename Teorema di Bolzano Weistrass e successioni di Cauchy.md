Sia $\{{a_{n}}\}_{n\in N}$ una [[Successioni]], si chiama sottosuccessione estratta da $\{{a_{n}}\}_{n\in N}$ ogni successione $\{{a_{n_{k}}}\}_{n\in N}$ dove $\{{a_{k}}\}_{k\in N}$ è una successione crescente.

Sia $\{{a_{n}}\}_{n\in N}$ una successione limitata in $[a,b]$, allora possiede almeno una sottosuccessione convergente ad un valore tra $a$ e $b$

>[!note]- Dimostrazione
>Sia $\{{a_{n}}\}_{n\in N}$ limitata tra a e b, consideriamo i due intervalli $\left[ a, \frac{a+b}{2} \right]$ e $\left[\frac{a+b}{2} , b\right]$, in almeno uno dei due cadono infiniti termini della successione $\{{x_{n}}\}_{n\in N}$, chiamo $\{{x_{n_{k}}}\}_{n\in N}$ i termini della successione contenuti in uno dei 2 sottointervalli e ripeto per dicotomia.
>
>Continuando si costruisce una successione crescente e limitata $\{{a_{k}}\}_{k\in N}$, una successione decrescente limitata $\{{b_{k}}\}_{k\in N}$ e una sottosuccessione $\{{x_{n_{k}}}\}_{n\in N}$  tale che $b_{k}-a_{k}=\frac{b-a}{2^{k+1}}$ e $x_{n_{k}}$ sono tutti contenuti in $[a_k,b_k]$.
>
>Ma allora visto che $\lim_{ n \to \infty } {a_{n}}=\lim_{ n \to \infty } {b_{n}}=x$ per il teorema del confronto anche la sottosuccesione $\{{x_{n_{k}}}\}_{n\in N}$  tende a x, che è compreso tra $[a,b]$

## Successione di Cauchy

Sia $\{{a_{n}}\}_{n\in N}$ una successione, si dice che $\{{a_{n}}\}_{n\in N}$ è di Cauchy se succede che$$
\forall {\epsilon} \gt {0},\exists {n_{0}} \in N \text{ | } \forall {n,m} \ge {n_{0}} \text{ si ha } |a_{n}-a_{m}|\lt\epsilon  $$
Cioè i termini di $\{{a_{n}}\}_{n\in N}$ si avvicinano tra loro al crescere di n.

>[!info] Teorema di Cauchy
>Una successione a valori reali è convergente in $R$ sse è di Cauchy

>[!tip]
>Si può dimostrare che l'[[assioma di Dedekind]] è equivalente al teorema di Cauchy



