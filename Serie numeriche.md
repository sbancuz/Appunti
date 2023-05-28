

---
tags: analisi_1, analisi_2
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

### [[Serie notevoli]]

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

### Convergenza semplice

Sia $E\subseteq J$ l'insieme dei punti $x$ in cui la serie converge puntualmente è detto insieme di convergenza puntuale o semplice. Nell'insieme $E$ risulta quindi ben definita la somma della seria
$$
f(x) = \sum_{i}^\infty{f_{i}(x)} = \lim_{ k \to \infty } {S_{k}(x)}
$$
### Convergenza totale

La serie di termine generale $f_{n}(x), x \in J$, converge totalmente in un intervallo $I\subseteq J$ se 
- $|f_{n}(x)|\leq a_{n}$ per ogni $n\in \mathbb N_{0}$ e $x \in I$ con $a_{n}\in \mathbb R$ 
- la serie numerica con termine $a_{n}$ è convergente

>[!note]
> La convergenza totale dipende dall'intervallo $I$, inoltre $f_{n}$ converge totalmente in $I$ <=> $\sum_{i}^\infty{sup|f_{n(x)}|} <\infty$ 

>[!warning]
>TOTALE in $I$ => ASSOLUTA $\forall {x} \in {I}$ => PUNTUALE $\forall {x} \in {I}$
>
>Ma non il contrario

