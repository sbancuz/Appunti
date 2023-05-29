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

#### Dimostrazione

Dobbiamo dimostrare che $\exists {\lim_{ \underline{x} \to \underline{x}_{0} }} f(\underline{x}) = f(\underline{x}_{0}) {}$

Siccome $f$ è differenziabile in $\underline{x}_{0}$, abbiamo che
$$
f(\underline{x}) = f(\underline{x}_{0}) + <\underline{a}, \underline{x} - \underline{x}_{0}> + \sigma(||\underline{x}-\underline{x}_{0}||)
$$
e quindi grazie alla diseguaglianza triangolare e a quella di Cauchy-Schwarz 
$$
0\leq |f(\underline{x})-f(\underline{x}_{0})| \leq ||\triangledown f(\underline{x}_{0})|| \cdot ||\underline{x}-\underline{x}_{0}||+ \sigma(||\underline{x}-\underline{x}_{0}||)
$$
Prendendo il limite per $\underline{x}\to \underline{x}_{0}$ si ottiene
$$
0\leq \lim_{ \underline{x} \to \underline{x}_{0} } {}|f(\underline{x})-f(\underline{x}_{0})| \leq\lim_{ \underline{x} \to \underline{x}_{0} } ||\triangledown f(\underline{x}_{0})|| \cdot ||\underline{x}-\underline{x}_{0}||+ \lim_{ \underline{x} \to \underline{x}_{0} }\sigma(||\underline{x}-\underline{x}_{0}||) = 0+0 = 0
$$
e quindi concludiamo che 
$$
\lim_{ \underline{x} \to \underline{x}_{0} } {}|f(\underline{x})-f(\underline{x}_{0})| = 0
$$
### Formula del gradiente

Sia $A\subseteq \mathbb R^n$ aperto, $f_:A\to \mathbb{R}$ differenziabile.  Allora per ogni [[Versori]] $\underline{v}\in \mathbb R^n$ esiste la derivata direzionale in $\underline{x}_{0}$ lungo la direzione $\underline{v}$ e inoltre
$$
\frac{ \partial f }{ \partial \underline{v} } = <\triangledown f(\underline{x}_{0}), \underline{v}>
$$

#### Dimostrazione

Siccome $f$ è differenziabile in $\underline{x}_{0}$, abbiamo che 
$$
f(\underline{x}_{0} + \underline{h}) = f(\underline{x}_{0}) + <\triangledown f(\underline{x}_{0}),\underline{h}> + \sigma(||\underline{h}||)
$$
per $\underline{h}\to0$ e applichiamo tale equazione a $\underline{h}=t\underline{v}$ per $t\in\mathbb{R}$ piccolo ottenendo 
$$
f(\underline{x}_{0} + t\underline{v}) = f(\underline{x}_{0}) + <\triangledown f(\underline{x}_{0}),t\underline{v}> + \sigma(t)
$$
e quindi
$$
\begin{align}
\frac{{f(\underline{x}_{0} + t\underline{v}) - f(\underline{x}_{0})}}{t}  & =  \frac{{<\triangledown f(\underline{x}_{0}),t\underline{v}>}}{t} + \frac{{\sigma(t)}}{t} \\
  & = {<\triangledown f(\underline{x}_{0}),\underline{v}>} + \frac{{\sigma(t)}}{t}
\end{align}
$$
e concludiamo che 
$$
\frac{ \partial f }{ \partial \underline{v} } = \lim_{ t \to 0 } {\frac{{f(\underline{x}_{0} + t\underline{v}) - f(\underline{x}_{0})}}{t} } = \lim_{ t \to 0 } {<\triangledown f(\underline{x}_{0}), \underline{v}>} + \lim_{ t \to 0 } \frac{{\sigma(t)}}{t} = <\triangledown f(\underline{x}_{0}), \underline{v}>
$$

### Direzione di massima e minima pendenza

Sia $A\subseteq \mathbb R^n$ aperto e $f:A\to \mathbb{R}$ differenziabile e con $\triangledown f(\underline{x}_{0}) \neq \underline{0}$. Allora per ogni versore $\underline{v} \in \mathbb R^n$ si ha che 
$$
\left|\frac{ \partial f }{ \partial \underline{v} } (\underline{x}_{0})\right| \leq ||\triangledown f(\underline{x}_{0})||
$$
e inoltre detti 
$$
\underline{v}_{MAX} = \frac{{\triangledown f(\underline{x}_{0})}}{{||{\triangledown f(\underline{x}_{0})}}||},\underline{v}_{MIN} = \frac{{-\triangledown f(\underline{x}_{0})}}{{||{\triangledown f(\underline{x}_{0})}}||},
$$
si ha che
$$
\frac{ \partial f }{ \partial \underline{v}_{MAX}(\underline{x}_{0}) } = ||\triangledown f(\underline{x}_{0})||,  \frac{ \partial f }{ \partial \underline{v}_{MIN}(\underline{x}_{0}) } = -||\triangledown f(\underline{x}_{0})||,  
$$

### Derivazione di funzioni composte

Sia $I\subseteq \mathbb{R}$ un intervallo e $A\subset \mathbb R^n$ uno aperto. Sia $\underline{r}:I->A$ una [[Curva in Rn]] regolare e $f:A\to \mathbb{R}$ una funzione differenziabile in $A$.
Detta $F:I\to \mathbb{R}$ la funzione composta definita per ogni $t\in I$ come $F(t)=(f\cdot \underline{r})(t) = f(\underline{r}(t))$, abbiamo che $F$ è derivabile in I e inoltre 
$$
F'(t) = <\triangledown (\underline{r}(t)), \underline{r}'(t)>
$$

