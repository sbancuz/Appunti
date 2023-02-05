 
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

>[!info] Teorema convergenza
>
>Ogni successione convergente è limitata
>>[!note]- Dimostrazione
Sia $a=\{a_n\}_{n\in N}$ e sia $\lim_{n\to \inf} a_n = l$ posso prendere $\epsilon=1$, $\exists n_0\in N\text{ | } \forall n\ge n_0$ si ha $|a_n-l| \le 1$ cioè $l-1\le a_n\le l+1$ quindi a è definitivamente limitata.
D'altra parte l'insieme $\{a_0,a_1,...,a_n\}$ è fubuti quindi ha massimo M e minimo m, dunque $\forall n\in N, a_n \le max\{M,l+1\} \text{ e } a_n \ge min\{m,l-1\}$ e perciò a è limitata

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

>[!info] Teorema di monotonia
>Siano $\{{a_{n}}\}_{n\in N}$ e $\{{b_{n}}\}_{n\in N}$ siccessioni convergenti tali che $\lim_{ n \to \infty } {a_{n}} = l$ e $\lim_{ n \to \infty } {b_{n}}=l_{1}$
>Se definitivamente $a_{n}\le b_{n}$ allora $l\le l_{1}$
>>[!note]- Dimostrazione
>>Sia $\{{c_{n}}\}_{n\in N}$ la successione $c_{n}=b_{n}-a_{n}$ allora $\{{c_{n}}\}_{n\in N}$ converge a $l_{1}-l$, e $\{{c_{n}}\}_{n\in N}$ è definitivamente positiva, quindi per la permanenza del segno $l_{1}-l\ge 0$

>[!info] Teorema del confronto
>Siano $\{{a_{n}}\}_{n\in N}$, $\{{b_{n}}\}_{n\in N}$, $\{{c_{n}}\}_{n\in N}$ successioni convergenti rispettivamente a $l,l_{1},l_{2}$.
>Se definitivamente $a_{n}\le b_{n}\le c_{n}$ allora $l\le l_{1}\le l_{2}$
>>[!warning]
>>Se   $a_{n}\lt b_{n}\lt c_{n}$ allora posso solo dire $l\le l_{1}\le l_{2}$
>

## Corollario

Siano $\{{a_{n}}\}_{n\in N}$, $\{{b_{n}}\}_{n\in N}$, $\{{c_{n}}\}_{n\in N}$ e $l=l_{_{2}}$ allora $\lim_{ n \to \infty } {b_{n}}=l$