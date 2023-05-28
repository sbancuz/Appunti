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