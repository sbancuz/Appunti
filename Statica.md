---
tags: [meccanica]
---
```math
||{"id":663367833301}||





```

$$
\overline{R}=\sum_{j}\overline{F_{j}}=0 = >
\left\{
\begin{align}
F_{x}=\sum_{j}F_{xj} \\
F_{y}=\sum_{j}F_{yj}
\end{align}
\right|
$$
Però questo vale solo nella statica dei punti, con i corpi rigidi invece ho le ![[Equazioni cardinali della statica]]
```math
||{"id":416637192677}||


```
$$
\overline{M_{o}}=(P_{1}-o)\land \overline{F_{1}}+(P_{2}-o)\land=(P-o)\land(\overline{F_{1}}+\overline{F_{2}})
$$
>[!warning]
>Questa formula vale solo se le due forze **NON** sono parallele

Se invece le 2 forze sono parallele avrò
```math
||{"id":787998994489}||


```


$$
\overline{M_{o}}=(P_{1}-o)\land \overline{F_{1}}+(P_{2}-o)\land \overline{F_{2}}=(P_{3}-P_{4})\land \overline{F_{1}}+(P_{4}-o)\land(\overline{F_{1}}+\overline{F_{2}})
$$
In pratica sto spostando una forza da una retta ad una sua parallela aggiungendo il suo $M_{tr}$
Un momento si ha quando in un sistema ho una coppia di forze.

Se $\overline{F_{1}} = -\overline{F_{2}}$
$$
\overline{M_{o}}=(P_{1}-o)\land \overline{F_{1}}= (P_{1}-o)\land \overline{F_{1}}=(P_{3}-P_{4})\land \overline{F_{1}}
$$

Dal punto di vista della statica se il punto di vista iniziale e finale del sistema sono uguali => Equipollenti.

Posso sostituire più forze con risultante nulla, basta che mantengo il momento di trasporto.
Se ho più corpi rigidi, allora per farli interagire devo usare i vincol

```math
||{"id":34014253536}||


```

### Sistema isostatico (Struttura)

$M_{GDLini}=N_{GDV}\implies N_{Reaz.Vinc.} \implies N_{incognite}\implies N_{equazioni}$

```math
||{"id":980566615006}||


```
### Sistema ipostatico (Meccanismo)

$M_{GDLini}>N_{GDV}\implies N_{equazioniEquilibrio}\implies L_{GDLresidui}\implies L_{equazioniEquilibrio}$

### Sistema iperstatico (Struttura)

$M<N \implies L=0 \implies$ non lo posso risolvere, ma nella realtà spesso si usano queste visto che nella realtà i corpi rigidi non esistono in quanto tutti i corpi sono deformabili

$n_{corpi}\implies$ GDL$_{iniziali}$ = $3\times n_{c}$ incognite. Se ho $i=0\dots n_{c}$
$$
\left\{
\begin{align}
 & \overline{R_{i}}=\sum_{j}\overline{F_{ij}}=0 \\
 & \overline{M_{oi}}=\sum_{j}(P_{ij}-o_{i})\land \overline{F_{ij}} =\sum_{j}(P_{ij}-o_{i})\land \overline{F_{ij}}+\sum_{k}\overline{C_{jk}}=0   
\end{align}\right|
$$
Con la $C$ che rappresenta la coppia di forze sul sistema