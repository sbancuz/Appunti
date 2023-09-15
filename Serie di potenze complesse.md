---
tags: analisi_2
---
### Serie di potenze complesse

Una serie di potenze in $\mathbb{C}$ è una serie di funzioni della forma
$$
\sum_{n=0}^\infty{a_{n}(z-z_{0})^{n}}
$$
con $a_{n}\in\mathbb{C}$ chiamati coefficienti della serie e $z_{0}\in\mathbb{C}$ chiamato centro della serie e $z\in\mathbb{C}$ è la variabile della serie.

>[!note]
>Tutte le proprietà di convergenza si trasportano anche per le serie di potenze complesse

### Teorema per calcolo del raggio di convergenza 

Data una serie di potenza $\sum a_{n} (z-z_{0})^{n}$ in $\mathbb{C}$ si verifica sempre una delle 3 seguenti opzioni:
- La serie converge solo per $z=z_{0}$
- La serie converge assolutamente $\forall {z} \in {\mathbb{C}}$ ed $R=\infty$
- Esiste $R>0$ detto raggio di convergenza tale che:
	-  La serie converge assolutamente $\forall {z} \in {\mathbb{C}}$ tale che $|z-z_{0}|<R$
	- La serie non converge $\forall {z} \in {\mathbb{C}}$ tale che $|z-z_{0}|>R$

Siccome $\mathbb{C}$ è un isomorfismo a $\mathbb{R}^{2}$ possiamo rappresentare ogni numero complesso su un piano cartesiano, e l'intorno di convergenza per una serie di potenze con centro $z_{0}\in\mathbb{C}$ e raggio $R>0$ è la palla 
$$
B_{R}(z_{0})\subset \mathbb{C}
$$
Per calcolare il raggio di convergenza rimane valido il teorema relativo al caso reale