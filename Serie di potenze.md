---
tags: analisi_2
---
Una serie di potenze reale è una serie di funzioni della forma
$$
\sum_{n=0}^\infty{a_{n}(x-x_{0})^{n}}
$$
con $a_{n}\in \mathbb R$ che viene chiamato coefficiente n-esimo della serie e $x_{0}\in \mathbb R$ che viene chiamato centro della serie

### Teorema del raggio di convergenza

Data la serie di potenze $\sum_{n=0}^\infty{a_{n}(x-x_{0})^{n}}$ si verifica sempre una delle 3 opzioni:

- La serie converge solo per $x=x_{0}$, cioè diciamo che il raggio di convergenza della serie è nullo
- La serie converge assolutamente su tutto $\mathbb R$ e in questo caso diciamo che il raggio di convergenza è infinito
- Esiste $R>0$ tale che:
	-  La serie converge assolutamente $\forall {x}  {}$ tale che $|x-x_{0}|<R$ 
	- La serie non converge per $x$ con $|x-x_{0}|>R$ 


>[!note]
>L'insieme di convergenza è sempre un intervallo simmetrico al centro della serie con raggio $R\in[0,\infty)\cup\{\infty\}$ a meno degli estremi dell'intervallo.
>Nel terzo caso bisogna controllare direttamente se c'è convergenza nei punti $x_{0}\pm R$

### Calcolo raggio di convergenza

Data la serie di potenze $\sum_{n=0}^\infty{a_{n}(x-x_{0})^{n}}$ abbiamo che, se uno dei seguenti limiti esiste:
$$
\begin{align}
R=\lim_{ n \to \infty } {|\frac{a_{n}}{a_{n+1}}|} \\
R =\lim_{ n \to \infty } {\frac{1}{\sqrt[n]{  |a_{n}|}}}
\end{align}
$$
allora la serie ha raggio di convergenza $R$

>[!warning]
>I criteri del rapporto e della radice per le serie numeriche sono legati a $\frac{1}{R}$

#### Dimostrazione

Grazie al teorema del raggio di convergenza è sufficiente verificare che la serie 
$$
\sum_{n=0}^\infty{|a_{n}(x-x_{0})^{n}|}
$$
converge per $|x-x_{0}|<R$ e che non converge per $|x-x_{0}|>R$

1) Osserviamo che tutte le serie di potenza convergono per $x=x_{0}$ e che per $x\neq x_{0}$ abbiamo
$$
\lim_{ n \to \infty } \frac{{|a_{n+1}(x-x_{0})^{n+1}|}}{|a_{n}(x-x_{0})^{n}|} = |x-x_{0}|\lim_{ n \to \infty } \frac{{|a_{n+1}|}}{a_{n}} = \frac{{|x-x_{0}|}}{R}
$$
e quindi le ipotesi sono dirette conseguenza del criterio del rapporto per la serie numerica

2) Osserviamo che $\forall {x} \in {\mathbb R}$
 $$
\lim_{ n \to \infty } {\sqrt[n]{|a_{n}(x-x_{0})^{n}|  }} = |x-x_{0}|\lim_{ n \to \infty } {\sqrt[n]{ a_{n} }} = \frac{|x-x_{0}|}{R}
$$
e quindi le ipotesi sono dirette conseguenze del criterio della radice per la serie numerica

### Teorema della convergenza totale

Data una serie di potenze $\sum_{n=0}^\infty{a_{n}(x-x_{0})^{n}}$ avente raggio di convergenza $0<R\leq+\infty$ si ha:

- se $R=\infty$ la serie converge totalmente in ogni intervallo chiuso $[a,b]\subseteq \mathbb R$
- se $R\in(0,\infty)$ la serie converge totalmente in ogni intervallo chiuso $[a,b]\subseteq(x_{0}-R,x_{0}+R)$

per ogni $a,b\in \mathbb R$ con $a<b$

### Corollario

Data la serie di potenza $a_{n}$ avente raggio di convergenza $0<R\leq \infty$ si ha che $p(x)$ è una funzione continua in $(x_{0}-R,x_{0}+R)$

### Corollario derivabilità termine a termine

Data una serie di potenze avente raggio $0<R\leq \infty$ si ha che $p(x)$ è una funzione derivabile in $(x_{0}-R,x_{0}+R)$ e 
$$
p'(x) = \sum_{n=1}^{\infty}na_{n}(x-x_{0})^{n-1}
$$
Inoltre la serie derivata è anch'essa una serie di potenze di centro $x_{0}$ con lo stesso raggio di convergenza $R$ e quindi infinitiva-mente derivabile. 

### Corollario integrabilità termine a termine

Data una serie di potenze avente raggio $0<R\leq \infty$ si ha che $p(x)$ soddisfa i seguenti asserti
- $p(x)$ ammette primitiva in $(x_{0}-R,x_{0}+R)$ che può essere calcolata termine a termine
$$
\int _{x_{0}}^{x}p(s) \, ds = \sum \frac{a_{n}}{n+1}(x-x_{0})^{n+1}
$$
ed è una serie di potenza centrata in $x_{0}$ e con raggio di convergenza $R$

-  per ogni intervallo $[a,b]\subset(x_{0}-R,x_{0}+R)$ la funzione $p(x)$ è integrabile su $[a,b]$ e
$$
\int _{a}^{b}p(x) \, dx = \sum\int _{a}^{b}a_{n}(x-x_{0})^{n} \, dx 
$$

### [[Serie di potenze complesse]]