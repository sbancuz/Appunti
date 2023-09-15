---
tags: analisi_1, analisi_2
---
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

### Serie armonica o di Riemann

La serie $\sum_{i=1}^\infty{\frac{1}{n}}$ si chiama serie armonica ed è una serie divergente, la forma generalizzata è $$
\sum_{i=1}^\infty{\frac{1}{n^\alpha}}=
\left\{
\begin{align}
\text{converge} & &  \alpha>1 \\
\text{diverge} &  & \alpha \leq 1
\end{align}
\right|
$$

>[!note]
>$$
>\sum \frac{1}{k^{2}} = \frac{\pi}{6}
>$$

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

=> [[Serie di potenze]]

### Serie logaritmica
$$
\sum_{n = 1}^\infty{\frac{x^{n}}{n}}
$$
Questa [[Serie di potenze]] ha centro $x_{0}=0$ , il raggio $R=1$ e coefficiente $a_{n} = \frac{1}{n}$
Converge assolutamente per $|x|<1$ e non converge per $|x|>1$, per $x= 1$ la serie coincide con la serie armonica e quindi diverge invece per $x=-1$ converge semplicemente per Leibniz.

Ha quindi insieme di convergenza puntuale $[-1, 1)$ e assoluta $(-1,1)$

### Serie esponenziale
$$
\sum_{n = 1}^\infty{\frac{x^{n}}{n!}}
$$
Questa [[Serie di potenze]] ha centro $x_{0}=0$ , il raggio $R=+\infty$ e coefficiente $a_{n} = \frac{1}{n!}$
Converge assolutamente in tutto $\mathbb R$

### [[Serie di Taylor]]

### [[Serie di Fourier]]

### Serie trigonometrica

Si dice serie trigonometrica l'espressione
$$
a_{0} + \sum a_{n} \cos(nx) + b_{n}\sin(nx)
$$
dove $a_{0},a_{n},b_{n}\in \mathbb{R}$ assegnati e $x\in\mathbb{R}$
