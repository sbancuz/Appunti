---
tags: [analisi_2]
---

Sia $k\in \mathbb N$ e $A \subseteq \mathbb R^{k}$, allora $f$ sarà una funzione di $k$ variabili a valori reali che associa ad ogni k-upla $\underline{x} = (x_{1},x_{2},x_{3},\dots ,x_{k})$ in $A$ un unico numero reale $f(\underline{x})$ cioè
$$
f:A\subseteq \mathbb  R^{k} \to \mathbb R \implies f(\underline{x}) = f(x_{1},x_{2},x_{3},\dots,x_{k}) 
$$
diciamo che $A$ è l'[[insieme]] di definizione o dominio di $f$. 

### [[Spazio Rn]]

### Curva di livello

Si dice insieme (o curva) di livello $c\in \mathbb R$ per la funzione $f:A\subseteq \mathbb R^n\to \mathbb R$ l'insieme
$$
I_{c} = \{ \underline{x}\in A:f(\underline{x}) = c \} \subseteq A
$$
quindi l'insieme dato dall'intersezione di un piano con $A$.
```math
||{"id":1238512795235}||


```

### [[Curva in Rn]]

### Classi

Sia $I\subseteq \mathbb R$ un'intervallo aperto. Una funzione $f: I\subseteq \mathbb R\to \mathbb R$ si dice di classe
- $\mathcal C^{0}$ su $I$ se $f$ è continua su $I$
- $\mathcal C^{1}$ su $I$ se $f$ è derivabile in $I$ e $f'$ è continua su $I$

### [[Calcolo integrale]] di linea

Sia $\underline{r}:[a,b] \subseteq \mathbb R\to \mathbb R^n$ una curva regolare con sostegno $\gamma$ e sia $f$ una funzione continua a valori reali definita su un sottoinsieme $A$ di $\mathbb R^n$ contenete $\gamma$ si dice integrale di linea di $f$ il numero
$$
\int _{\gamma}f \, ds = \int _{a}^{b}f(\underline{r}(t))||\underline{r}'(t)|| \, dt  
$$

>[!tip] Applicazioni
>- Massa => $M = \int _{\gamma}f \, ds$
>- Baricentro => $B_{i} = \frac{1}{M}\int _{a}^{b} r_{i}(t) \rho(\underline{r}(t))||\underline{r}'(t)||\, dt$


### [[Serie numeriche]]

### Continuità

Sia $\underline{x}_{0}\in A\subseteq \mathbb{R}^{n}$ con $A$ aperto e $f:A\to \mathbb{R}$. Diciamo che $f$ è continua in $\underline{x}_{0}$ se 
$$
\exists {\lim_{ \underline{x} \to \underline{x}_{0} } {f(\underline{x})}} = f(\underline{x}_{0})  {} 
$$
Inoltre $f$ è detta continua in $A$ se $f$ è continua in ogni $\underline{x}_{0}\in A$

### [[Calcolo differenziale per funzioni a più variabili]]