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
||{"id":1675817655606}||





```



