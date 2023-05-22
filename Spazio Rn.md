---
tags: analisi_2, gal
---

Definisco $\mathbb R^{n}=\mathbb R \times \dots \times \mathbb R= \{\underline{x}=\left( x_{1}\dots x_{n} \right)^{T} : x_{i} \in \mathbb R\}$

>[!tip]
>$\mathbb R^{n}$ è uno spazio vettoriale di dimensione n la cui base canonica è
>$$
>\underline{e}_{1} = \left( \begin{matrix} 1\\0\\0\\ \vdots\\ 0\end{matrix} \right) 
>\underline{e}_{2} = \left( \begin{matrix} 0\\1\\0\\ \vdots\\ 0\end{matrix} \right) 
>\dots
>\underline{e}_{n} = \left( \begin{matrix} 0\\0\\0\\ \vdots\\ 1\end{matrix} \right) 
>$$

### Diseguaglianza triangolare
$$
\forall {\underline{x}} \underline{y}\in  {\mathbb  R^{n}} \implies| | \underline{x}+ \underline{y}| | \leq ||\underline{x}| | + | | \underline{y} | |
$$

### Diseguaglianza di Cauchy-Schwarz
$$
\forall {\underline{x}} \underline{y}\in  {\mathbb  R^{n}} \implies|  <\underline{x}+ \underline{y}> | \leq ||\underline{x}| |\times | | \underline{y} | |
$$
### Palla centrata

Dato $\underline{x}_{0}\in \mathbb R^{n}$ e un numero reale $r>0$, definiamo "palla" centrata in $\underline{x}_{0}$ di raggio $r$ come 
$$
B_{r}(x_{0}) = \{\underline{x}\in \mathbb  R^{n} : dist(\underline{x},\underline{x}_{0})<r\}
$$
### Interno, punti di frontiera e esterno di Rn

Sia $E$ un [[sottoinsieme]] di $\mathbb R^{n}$ e sia $\underline{x}_{0}\in \mathbb R^{n}$. Si dice che 
- $\underline{x}_{0}$ è interno a $E$ se esiste $r>0$ tale che $B_{r}(\underline{x}_{0})\subseteq E$, e l'insieme dei punti interni di $E$ formano la sua parte interna $Int(E)$
- $\underline{x}_{0}$ è punto di frontiera di $E$ se $\forall {}  {}r>0$ si ha che $B_{r}(\underline{x}_{0})\cap E\neq 0$, e $B_{r}(\underline{x}_{0}) \setminus E = B_{r}(\underline{x}_{0})\cap E^{c}\neq 0$
- $\underline{x}_{0}$ è esterno a $E$ se $\underline{x}_{0}\notin E$ ed esiste $r>0$ tale che $B_{r}(\underline{x}_{0})\subseteq E^{c}$


```math
||{"id":906664436889}||


```

$$
\begin{align}
\underline{x}_{0}\in E, Int(E)\\
\underline{x}_{1}\notin E, Ext(E)\\
\underline{x}_{2}\in E, \text{Bordo}(E)\\
\underline{x}_{3}\notin E, \text{Bordo}(E)
\end{align}
$$

### Insiemi aperti/chiusi

Sia $E\subseteq \mathbb R^n$ e si dica
- aperto se $\forall {\underline{x}\in E}  {}$ si ha che $\underline{x}$ è intorno ad E
- chiuso se $E^{c}$ è aperto

>[!tip]
>Esistono insiemi che non sono ne aperti ne chiusi

### Intervalli

$\forall {a,b} \in {\mathbb R}$ con $a<b$ definiamo:
- intervallo chiuso tra $a$ e $b$ : $[a,b]=\{ x\in\mathbb R:a\leq x\leq b \}$
- intervallo aperto tra $a$ e $b$ : $(a,b)=\{ x\in\mathbb R:a< x< b \}$
- intervallo semiaperto a destra : $[a,b)=\{ x\in\mathbb R:a\leq x< b \}$
- intervallo semiaperto a sinistra : $(a,b]=\{ x\in\mathbb R:a< x\leq b \}$

### Punto di accumulazione

Sia $E\subseteq \mathbb R^n$ e $\underline{x}_{0}\in \mathbb R^n$. Diciamo che $\underline{x}_{0}$ è un punto di accumulazione per $E$ se $\forall {r>0}  {}$ si ha che $(B_{r}(\underline{x}_{0})\cap E) \setminus \{ \underline{x}_{0} \} \neq 0$

>[!note]
>Anche i punti di bordo possono essere di accumulazione


### Insiemi limitati

$E\subseteq \mathbb R^n$ è detto limitato se esiste un raggio $r>0$ tale che $E\subseteq B_{r}(\underline{O})$ dove $O$ è l'origine in $\mathbb R^n$. Altrimenti $E$ si dice illimitato.** 

### Insiemi connessi per archi

Un insieme $E\subseteq \mathbb R^n$ si dice connesso per archi se $\forall {\underline{x},\underline{y}} \in  {E}$ esiste una [[Curva in Rn]] continua $\underline{r}(t)$ contenuta in E con estremi $\underline{x},\underline{y}$
