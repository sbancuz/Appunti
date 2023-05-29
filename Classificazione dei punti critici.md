---
tags: analisi_2
---
I punti critici dipendono dal segno della forma quadratica ([[Ottimizzazione per funzione di più variabili]]) indotta dalla matrice Hessiana nel punto critico.

### Matrice di rappresentazione

Per ogni forma quadratica $q\in\mathbb R^n$ esiste una matrice simmetrica $A\in\mathbb M_{n\times n}(\mathbb{R})$ che si chiama matrice di rappresentazione tale che
$$
q(\underline{x}) = \left< \underline{x}, A\underline{x} \right> 
$$
Per ogni $A$ simmetrica abbiamo che $\underline{q}(\underline{x}) = \left< \underline{x}, A\underline{x} \right>$ è una forma quadratica in $\mathbb R^n$ inoltre abbiamo che 
$$
\lambda_{max}||\underline{x}||^{2} \geq \left< \underline{x}, A\underline{x} \right> \geq \lambda_{min}||\underline{x}||^{2} 
$$
dove $\lambda$ sono autovalori di $A$.

### Segno di q

Sia $q$ una forma quadratica in $\mathbb R^n$ con matrice di rappresentazione $A$. Definiamo il segno di $q$ come:
- definita positiva/negativa => tutti gli autovalori di $A$ sono strettamente positivi/negativi
- semi-definita positiva/negativa =>  tutti gli autovalori di $A$ sono $\geq,\leq 0$ 
- indefinita => quando $A$ ammette sia un autovalore negativo e uno positivo

### Teorema della matrice Hessiana

Siano $A\subseteq \mathbb R^n$ aperto, $f\in\mathcal C^{2}(A)$ e $\underline{x}_{0}\in A$ critico di $f$. Sia $q:\mathbb R^n\to \mathbb{R}$ la forma indotta dalla matrice Hessiana $H_{f}(\underline{x}_{0})$. Abbiamo che
1) Se q è definita positiva, allora $\underline{x}_{0}$ è punto di minimo
2) Se q è definita negativa, allora $\underline{x}_{0}$ è punto di massimo
3) Se q è indefinita, allora $\underline{x}_{0}$ è di sella

>[!note]
>In caso la funzione sia semi-definita il teorema non ci dice nulla

#### Dimostrazione

La matrice Hessiana $H_{f}(\underline{x}_{0})$ è:
1) simmetrica per Schwarz
2) ha tutti gli autovalori reali e positivi siccome la forma quadratica indotta da $H_{f}$ è definita positiva

Da 1) deduciamo che 
$$
q(\underline{h}) = \left< \underline{h},H_{f}(\underline{x}_{0} )\underline{h} \right> \geq \lambda_{min}||\underline{h}||^{2}
$$
dove $\lambda_{min}$ denota l'autovalore più piccolo. Dato che $\underline{x}_{0}$ è un punto critico, dalla formula di Taylor al secondo ordine otteniamo che
$$
f(\underline{x}_{0}+\underline{h}) - f(\underline{x}_{0}) = \cancel{\left< \triangledown f(\underline{x}_{0}), \underline{h} \right> } + \frac{1}{2}q(\underline{h}) + \sigma(||\underline{x}||^{2}) \geq \frac{1}{2} \lambda_{min}||\underline{h}||^{2} + \sigma(||\underline{h}||^{2})
$$
per $||\underline{h}||\to0$.

Per la definizione di $\sigma$-piccolo abbiamo che 
$$
\lim_{ \underline{h} \to 0 } \frac{{\sigma(||\underline{h}||^{2})}}{||\underline{h}||^{2}} = 0
$$
e quindi $\exists {\delta} > {0}$ tale che, se $||\underline{h}||<\delta$ e $\underline{h}\neq 0$ allora
$$
 \frac{|{\sigma(||\underline{h}||^{2})|}}{||\underline{h}||^{2} } < \frac{1}{4}\lambda_{min}
$$
e siccome da 2) $\lambda_{min}>0$  si può concludere che
$$
\begin{align}
f(\underline{x}_{0}+\underline{h}) - f(\underline{x}_{0})  & \geq \frac{1}{2} \lambda_{min}||\underline{h}||^{2} + \sigma(||\underline{h}||^{2}) \\
  & \geq \frac{1}{2} \lambda_{min}||\underline{h}||^{2} - \frac{1}{4} \lambda_{min}||\underline{h}||^{2} \\
   &  = \frac{1}{4}\lambda_{min}||\underline{h}||^{2} \geq 0
\end{align}
$$
$\forall {\underline{h}} \in {B_{\delta}(0)}$ tale che $\underline{x}_{0}+\underline{h}\in A$, che implica che, $\underline{x}_{0}$ è un punto minimo locale di $f$

### Convessità

Sia $f:\mathbb{R}^{2} \to \mathbb{R}\in \mathcal C^{2}(\mathbb{R}^{2})$. Diciamo che $f$ è convessa (concava) se $\forall {(x,y)} \in {\mathbb{R}^{2}}$ la matrice Hessiana è definita positiva o semi-definita positiva (o negativa per concava) 

Sia $f:\mathbb{R}^{2} \to \mathbb{R}\in \mathcal C^{2}(\mathbb{R}^{2})$ e $(x_{0},y_{0})$ un punto critico di $f$ allora:
- Se $f$ è convessa su $\mathbb{R}^{2}$ allora il punto è un punto di minimo assoluto
- Se $f$ è concava su $\mathbb{R}^{2}$ allora il punto è di massimo assoluto

>[!note]
>Se $H_{f}$ è semi-definita positiva o negativa solo nel punto critico non possiamo concludere nulla
>
> Se $H_{f}$ è semi-definita ovunque positiva o negativa su $\mathbb{R}^{2}$ allora tutti i punti critici sono estremanti e per giunta assoluti