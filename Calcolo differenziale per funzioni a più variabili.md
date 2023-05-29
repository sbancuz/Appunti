---
tags: analisi_2
---
==>[[Limiti di funzioni a più variabili]]

Per il caso ad una variabile ([[Calcolo differenziale]]) la derivata è definita come 
$$
f'(x_{0}) = \lim_{ h \to 0 } \frac{{f(x_{0}+h) - f(x_{0})}}{h}
$$
Il problema è quando si espande questa definizione per più variabili, in quanto $\underline{h}$ sarebbe un vettore, e quindi non si può usare per dividere.

### Derivate parziali

Si può quindi differenziare la funzione in rispetto ad una sola variabile alla volta e trattare le altre come costanti della funzione.

Sia $A\subseteq \mathbb{R}^{2}$ aperto, $f:A\to \mathbb{R}$ e $\underline{x}_{0}=(x_{0},y_{0})\in A$ diciamo che:
- la derivata parziale di $f$ rispetto a $x$ nel punto $\underline{x}_{0}$ è
$$
f'_{x} = \frac{ \partial f }{ \partial x } (x_{0},y_{0}) = \lim_{ h \to 0 } \frac{{f(x_{0}+h, y_{0}) - f(x_{0},y_{0})}}{h}
$$
- la derivata parziale di $f$ rispetto a $y$ nel punto $\underline{x}_{0}$ è
$$
f'_{y} = \frac{ \partial f }{ \partial y } (x_{0},y_{0}) = \lim_{ h \to 0 } \frac{{f(x_{0}, y_{0}+h) - f(x_{0},y_{0})}}{h}
$$
>[!warning]
>A differenza del caso $n=1$, l'esistenza della derivata parziale non implica la continuità di $f$ nel punto $\underline{x}_{0}$

### Derivabilità

$f$ si dice derivabile in $\underline{x}_{0}$ se esistono tutte le derivate parziali $i$-esime di $\frac{ \partial f }{ \partial x_{i} }$, inoltre si dice derivabile in $A'\subseteq A$ se $f$ è derivabile in tutti i punti di $A'$

### Gradiente

Sia $A\subseteq \mathbb{R}^{n}$ aperto, $f:A\to \mathbb{R}$, se $f$ è derivabile in $\underline{x}_{0}$, allora diciamo che il gradiente di $f$ è:
$$
\triangledown f(\underline{x}_{0}) = \left( \begin{align}
\frac{ \partial f }{ \partial x_{1} } & (\underline{x}_{0}) \\
\frac{ \partial f }{ \partial x_{2} } & (\underline{x}_{0}) \\
 & \vdots \\
\frac{ \partial f }{ \partial x_{n} } & (\underline{x}_{0})
\end{align} \right) \in \mathbb{R}^{n}
$$
### Derivata direzionale

Sia $A\subseteq \mathbb R^n$ aperto, $f:A\to \mathbb{R}$, sia $\underline{v}\in \mathbb R^n$ un [[Versori]]. Diciamo che la derivata direzionale di $f$ in $\underline{x}_{0}$ nella direzione individuata da $\underline{v}$ è
$$
D_{\underline{v}} = \frac{ \partial f }{ \partial \underline{v} } (\underline{x}_{0}) = \lim_{ t \to 0 } \frac{{f(\underline{x}_{0} + t\underline{v}) - f(\underline{x}_{0})}}{t}
$$
purché il limite esista finito.

### Differenziabilità

Sia $A\subseteq \mathbb R^n$ aperto, $f_:A\to \mathbb{R}$. Diciamo che $f$ è differenziabile in $\underline{x}_{0}$ se $\exists {\underline{a}} \in {\mathbb R^n}$ tale che prendendo un $\underline{h}$ e la funzione resto
$$
R(\underline{h}) = f(\underline{x}_{0}+\underline{h}) - f(\underline{x}_{0}) - <\underline{a}, \underline{h}>
$$
si ha che
$$
\lim_{ h \to 0 } \frac{{R(\underline{h})}}{||\underline{h}||} = 0
$$
o equivalentemente, ponendo $\underline{x} = \underline{x}_{0} +\underline{h}$
$$
f(\underline{x}) = f(\underline{x}_{0}) + <\underline{a}, \underline{x} - \underline{x}_{0}> + \sigma(||\underline{x}-\underline{x}_{0}||)
$$
Inoltre si può verificare che $a = \triangledown f(\underline{x}_{0})$

>[!note]
>Se $f$ è differenziabile in $\underline{x}_{0}$ allora
>1) $f$ è derivabile in $\underline{x}_{0}$
>2) esiste un iperpiano tangente al grafico di $f$ nel punto $(\underline{x}_{0},f(\underline{x}_{0}))$ e tale che l'iperpiano ha equazione
>$$
> z = f(\underline{x}_{0}) + <\triangledown f(\underline{x}_{0}), \underline{x} - \underline{x}_{0}>
>$$

### Verificare funzione differenziabile

Sia $A\subseteq \mathbb R^n$ aperto, $f_:A\to \mathbb{R}$ derivabile.  Diciamo che $f$ è di classe $\mathcal C'$ in $A$ se tutte le derivate parziali di $f$ esistono e sono funzioni continue in $A$

### Teorema del differenziale totale

Sia $A\subseteq \mathbb R^n$ aperto, $f\in \mathcal C'(A)$, allora è differenziabile in $A$

### Condizione necessaria per la differenziabilità

Sia $A\subseteq \mathbb R^n$ aperto, $f_:A\to \mathbb{R}$ differenziabile.  Allora $f$ è continua in $\underline{x}_{0}$