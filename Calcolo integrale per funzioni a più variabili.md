---
tags: analisi_2
---
### [[Calcolo integrale]] di linea

Sia $\underline{r}:[a,b] \subseteq \mathbb R\to \mathbb R^n$ una curva regolare con sostegno $\gamma$ e sia $f$ una funzione continua a valori reali definita su un sottoinsieme $A$ di $\mathbb R^n$ contenete $\gamma$ si dice integrale di linea di $f$ il numero
$$
\int _{\gamma}f \, ds = \int _{a}^{b}f(\underline{r}(t))||\underline{r}'(t)|| \, dt  
$$

>[!tip] Applicazioni
>- Massa => $M = \int _{\gamma}f \, ds$
>- Baricentro => $B_{i} = \frac{1}{M}\int _{a}^{b} r_{i}(t) \rho(\underline{r}(t))||\underline{r}'(t)||\, dt$

L'integrale di linea fornisce l'area della superficie tra $\gamma$ e $Gr_{f}$

### Integrale multiplo

L'integrale multiplo su insiemi $A$ k-dimensionali con $k>1$ con notazione
$$
\int _{A}f(\underline{x}) \, d\underline{x} 
$$
calcola il volume della regione racchiusa tra il dominio $A$ della funzione e $Gr_{f}$ un analogia al caso ad una variabile

### Integrale doppio

Sia $k=2$. L'integrale multiplo viene chiamato integrale doppio. Iniziamo col definire alcune regioni $D\subseteq \mathbb{R}^{2}$ adatte all'integrazione:
