---
tags: [analisi_1]
---
Sia $\{{a_{n}}\}_{n\in N}$ una successione, si può definire una seconda successione $\{{s_{n}}\}_{n\in N}$ in questo modo:$$
\begin{align}
s_{0} & =a_{0}\\
s_{1} & =a_{0}+a_{1}\\
s_{2} & =a_{0}+a_{1}+a_{2} \\
 & \dots\\
s_{n} & =a_{0}+a_{1}+\dots+a_{n} = \sum_{i=0}^na_{i} = s_{n-1}+a_{n}\\
\end{align}
$$La successione $\{{s_{n}}\}_{n\in N}$ si chiama successione delle somme parziali di $\{{a_{n}}\}_{n\in N}$
Poiché $\{{s_{n}}\}_{n\in N}$ è una successione posso calcolare il limite per n->$\infty$
$$
\lim_{ n \to \infty } {\sum_{i=0}^nai} = \sum_{i=0}^\infty{a_{i}}

$$
La scrittura $\sum_{i=0}^\infty{a_{i}}$ si chiama SERIE a termini $a_{i}$
Poiché una serie è un limite di una successione, una serie può essere regolare o irregolare.

Se la serie $\sum_{i=0}^\infty{a_{i}}$ è regolare e convergente, allora converge alla sua somma $s$

## Studio del carattere

Poiché una serie è un limite il carattere di una serie può essere:
	• regolare convergente
	• regolare divergente
	• irregolare

### Condizione necessaria di convergenza:

Se $\sum_{i=0}^\infty{a_{i}}$ converge allora $\lim_{ n \to \infty } {a_{n}}=0$ 
ovvero se $\lim_{ n \to \infty } {a_{n}}\neq 0$ allora $\sum_{i=0}^\infty{a_{i}}$ non converge

Quindi questo criterio serve a provare la NON convergenza

>[!note]- Dimostrazione
>Supponiamo che $s_{n}=\sum_{i=0}^\infty{a_{i}}$ converga, si ha che la successione $\{{s_{n}}\}_{n\in N}$ converge, sia $s$ il suo limite.
>Inoltre $a_n=s_{n}-s_{n-1}$, quindi il $\lim_{ n \to \infty } {a_{n}}=\lim_{ n \to \infty } {s_{n}-s_{n-1}}=s-s=0$

![[Criterio del confronto per le serie]]

![[Criterio del confronto asintotico per le serie]]

![[Criterio della radice per le serie]]

![[Criterio del rapporto per le serie]]


## Proprietà

Sia $\sum_{i=0}^\infty{a_{i}}$ una serie convergente, allora è convergente anche $\sum_{i=1}^\infty{a_{i}}$ lo è,
inoltre $\lim_{ n \to \infty } {\sum_{i=n}^\infty{a_{i}}}=0$

### Serie geometrica

$$
\sum_{i=0}^\infty{q^i}=\lim_{ n \to \infty } \frac{{1-q^{n+1}}}{1-q}=
\left\{\begin{align}
+\infty & &   q \geq 1 \\
\frac{1}{1-q} & &  -1<q<q \\
irregolare &  & q \lt -1\\
\end{align}
\right|
$$

### Serie armonica

La serie $\sum_{i=1}^\infty{\frac{1}{n}}$ si chiama serie armonica ed è una serie divergente, la forma generalizzata è $$
\sum_{i=1}^\infty{\frac{1}{n^\alpha}}=
\left\{
\begin{align}
\text{converge} & &  \alpha>1 \\
\text{diverge} &  & \alpha \leq 1
\end{align}
\right|
$$

### Serie a termini non negativi

Sia $\{{a_{n}}\}_{n\in N}$ una successione non negativa, cioè $\forall n \in N, a_{n}\geq 0$ allora $\sum_{i=0}^\infty{a_{n}}$ o converge o diverge, quindi non può essere irregolare

>[!note]- Dimostrazione
>Sia $s_{n}=\sum_{i=0}^\infty{a_{i}}$, allora $\{{s_{n}}\}_{n\in N}$ è crescente monotona e per il teorema di monotonia o è convergente o è divergente

Questo teorema vale anche se $\{{a_{n}}\}_{n\in N}$ è definitivamente non negativa o definitivamente non positiva

### Serie telescopiche

Sia $\{{a_{n}}\}_{n\in N}$ una succession, allora la serie $\sum_{i=0}^\infty{a_{n}-a_{n+1}}$ si chiama serie telescopica che in generale $s_{n}=a_{0}-l$

Se $a_{n}$ converge allora la successione $\{{a_{n}-a_{n+1}}\}_{n\in N}=0$

### Serie somma

Siano $\{{a_{n}}\}_{n\in N}$ e $\{{b_{n}}\}_{n\in N}$ successioni definitivamente positive, si chiama serie somma di $\{{a_{n}}\}_{n\in N}$ e $\{{b_{n}}\}_{n\in N}$ la serie $\sum_{i=0}^\infty{(a_{n}+b_{n})}$

Se $\sum_{i=0}^\infty{a_{n}}$ converge e $\sum_{i=0}^\infty{b_{n}}$ converge allora la somma converge a $l+l_{1}$
Se $\sum_{i=0}^\infty{a_{n}}$ diverge e $\sum_{i=0}^\infty{b_{n}}$ converge allora la somma diverge
Se $\sum_{i=0}^\infty{a_{n}}$ diverge e $\sum_{i=0}^\infty{b_{n}}$ diverge allora la somma diverge

>[!warning]
>Se le due serie divergono una a $\infty$ e l'altra a $-\infty$ allora non si può dire nulla

## Serie a termini di segno variabile

Sia $\{{a_{n}}\}_{n\in N}$ una successione qualunque, si dice che $\sum_{i=0}^\infty{a_{n}}$ converge assolutamente se  la serie $\sum_{i=0}^\infty{|a_{n}|}$ converge.

Se la serie  $\sum_{i=0}^\infty{a_{n}}$ converge assolutamente allora converge.

>[!note]- Dimostrazione
>Data $\{{a_{n}}\}_{n\in N}$ consideriamo le somme $s_{n}^+$ che è la somma dei termini positivi e $s_{n}^-$ che è la somma dei termini negativi
>Invece sia $s_{n}=\sum_{i=0}^\infty{a_{i}}$ è la somma parziale di tutti i termini.
>
>Si ha che $s_{n}=s_{n}^++s_{n}^-$ e se provo che la somma converge allora $s_{n}$ convergerà.
>
>Osservo che $s_{n}^+$ è una successione a termini ppositivi o nulli, inoltre per la disuguaglianza triangolare si ha $s_{n}^+\leq \sum_{i=0}^n{|a_{i}|}$ e $-s_{n}^-\leq \sum_{i=0}^n{|a_{i}|}$.
>
>Ma per ipotesi $\sum_{i=0}^\infty{|a_{i}|}$ converge, quindi $\{{s_{n}^+}\}_{n\in N}$ e $\{{s_{n}^-}\}_{n\in N}$ sono successioni crescenti e limitate, e per il teorema di monotonia convergono.

![[Criterio di Leibniz]]