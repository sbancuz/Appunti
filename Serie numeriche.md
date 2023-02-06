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

## Criterio del confronto

Siano $\{{a_{n}}\}_{n\in N}$ e $\{{b_{n}}\}_{n\in N}$ successioni tali che definitivamente siano non negative e sia $a_{n}\leq b_{n}$ allora:
	1. se $\sum_{i=0}^\infty{b_{n}}$ converge, allora $\sum_{i=0}^\infty{a_{n}}$ converge
	2. se $\sum_{i=0}^\infty{a_{n}}$ diverge, allora $\sum_{i=0}^\infty{b_{n}}$ diverge

>[!note]- Dimostrazione
>1. Sia $n_{0}$ tale che $\forall {n} \geq {n_{0}}$ si abbia $0\leq a_{n}\leq b_{n}$
>	e siano $s_{n_{1}}=\sum_{i=n_{0}}^\infty{a_{i}}$ e $s_{n_{2}}=\sum_{i=n_{0}}^\infty{b_{n}}$ con $n\geq n_{0}$,
>	allora $\forall {n} \geq {n_{0}}$ si ha che $s_{n_{1}}\leq s_{n_{2}}$ e poiché gli addendi in$s_{n_{1}}$ sono tutti $\leq$ di quelli di $s_{n_{2}}$ posso applicare il teorema del confronto alle successioni $s_{n_{1}}$ e $s_{n_{2}}$
>	Quindi $0\leq \sum_{i=0}^\infty{a_{n}}=\sum_{i=0}^{n_{0}-1}{a_{i}}+\sum_{i=n_{0}}^\infty{a_{i}}\leq\sum_{i=0}^{n_{0}-1}{a_{i}}+\lim_{ n \to \infty } {s_{n_{2}}}$
>	Se $\lim_{ n \to \infty } {s_{n_{2}}}$ esiste ed è finito
>2. Segue direttamente da 1. è l'opposto

## Criterio del confronto asintotico

Siano $\{{a_{n}}\}_{n\in N}$ e $\{{b_{n}}\}_{n\in N}$ non definitivamente negative e sia $a_{n}\sim b_{n},n\to \infty$ allora: $\sum a_{n}$ e $\sum b_{n}$ hanno lo stesso carattere

>[!note]- Dimostrazione
>Sappiamo che $\lim_{ n \to \infty } {\frac{a_{n}}{b_{n}}}=1$ e quindi $\forall {\epsilon} > {0}, \exists {n_{0}}$ tale che $\forall {n} \geq {n_{0}}$ ho che $-\epsilon<\frac{a_{n}}{b_{n}}-1< \epsilon$
>Se scelgo $\epsilon = \frac{1}{2}$ ho che $\exists {n_{0}}$ tale che $\forall {n} \geq {no}$ ho che $\frac{1}{2}< \frac{a_{n}}{b_{n}}< \frac{3}{2}$.
>
>Ora posso applicare il teorema del confronto alle 3 successioni.
>Se $\sum_{i=0}^\infty{b_{n}}$ converge allora $\sum_{i=0}^\infty{a_{n}}$ converge, se $\sum_{i=0}^\infty{a_{n}}$ diverge allora $\sum_{i=0}^\infty{b_{n}}$ diverge

## Criterio della radice

Sia $\{{a_{n}}\}_{n\in N}$ una successione non negativa, se esiste il $\lim_{ n \to \infty } {\sqrt[n]{ a_{n} }}$ allora 
	• se $l<1$, $\sum_{i=0}^\infty{a_{i}}$ converge
	• se $l>1$, $\sum_{i=0}^\infty{a_{i}}$ diverge
	• se $l=1$ non si sa

>[!note]- Dimostrazione
> Sia $\lim_{ n \to \infty } {\sqrt[n]{ a_{n} }}<1$ allora $\forall {\epsilon} \geq {0}, \exists {n_{0}} \text{ tale che } \forall {n} \geq {n_{0}}$, $l-\frac{\epsilon}{2}<\sqrt[n]{ a_{n} }<l+\frac{\epsilon}{2}$ e quindi $\sqrt[n]{ a_{n} }<(1-\epsilon)+\frac{\epsilon}{2}=1+\frac{\epsilon}{2}$ 
> Allora $a_{n}<\left( 1-\frac{\epsilon}{2} \right)^n$ che converge e per il teorema del confronto anche $\{{a_{n}}\}_{n\in N}$ convergerà

## Criterio del rapporto

Sia $\{{a_{n}}\}_{n\in N}$ una successione positiva, se esiste il $\lim_{ n \to \infty } {\frac{{ a_{n+1} }}{a_{n}}}$ allora 
	• se $l<1$, $\sum_{i=0}^\infty{a_{i}}$ converge
	• se $l>1$, $\sum_{i=0}^\infty{a_{i}}$ diverge
	• se $l=1$ non si sa

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

## Criterio di Leibniz

Sia data $\sum_{i=0}^\infty{(-1)^na_{n}}$ allora se:
	1. $\{{a_{n}}\}_{n\in N}$ è a termini definitivamente positivi
	2. $\lim_{ n \to \infty } {a_{n}}=0$
	3. $\{{a_{n}}\}_{n\in N}$ è definitivamente decrescente

Si ha che la serie converge

Inoltre si ha che $|\sum_{i=n}^\infty{(-1)^na_{n}|}\leq a_{n}$ cioè l'errore che si commette approssimando la serie troncandola al termine $a_n$ è minore dell'ultimo termine considerato