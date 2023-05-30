---
tags: analisi_2
---
### Teorema di esistenza e unicità locale per il problema di Cauchy del primo ordine

Siano $A=I\times B\subseteq \mathbb{R}^{2}$ per un intervallo aperto $I$ e un insieme aperto $B$, $\underline{x}_{0}\in A$ e $f:A\to \mathbb{R}$ continua. Consideriamo il problema di Cauchy:
$$
\begin{cases}
y'(x  = f(x,y(x)))  & x\in I\\
y(x_{0} ) = y_{0}
\end{cases}
$$
Abbiamo che:
1) il problema di Cauchy ammette una soluzione $y\in\mathcal C'(J)$ definita su un intervallo $J\subseteq I$ con $x_{0}\in J$
2) se $\exists {\delta} > {0}$ tale che $\frac{ \partial f }{ \partial y }$ esiste unica ed è continua in $B_{\delta}(\underline{x}_{0})$ allora $J$ si può prendere sufficientemente piccolo

### Prolungabilità delle soluzioni

Consideriamo un problema di Cauchy sulla striscia $A=(\alpha ,\beta)\times \mathbb{R}$ con $-\infty\leq\alpha<\beta\leq \infty$ e $f\in\mathcal C^{0}(A)$ tale che $\exists {f_{y}}\in  {}\mathcal C^{0}(A)$ e sia $y:J\to \mathbb{R}$ la sua unica soluzione con $J$ intervallo massimale di definizione. Abbiamo che:
1) se esistono due costanti $k_{1},k_{2}\geq 0$ tali che $|f(x,y)|\leq k_{1}+k_{2}|y|$ allora $J = (\alpha,\beta)$
2) se $y$ è limitata su $J$ allora $J=(\alpha,\beta)$