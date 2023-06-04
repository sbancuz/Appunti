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
Con la $C$ che rappresenta la coppia di forze sul sistema.

## Come agiscono le forze all'interno del sistema?

Le forze sul sistema viaggiano alla velocità del suono all'interno del materiale

```math
||{"id":658219379040}||





```
$$
\begin{cases}
V_{A}+V_B = F \\
H_{A} = F \\
Fa = V_{B}L
\end{cases} \implies \begin{cases}
H_{A} = F \\
V_{B} = \frac{Fa}{L} \\
V_{A}=  \frac{Fb}{L}
\end{cases}
$$

In ogni sottosistema che si può creare ci deve essere equilibrio
$$
\begin{cases}
H=H_{A} \\
V=V_{A} \\
M=V_{A}x \\
\end{cases}
$$

```math
||{"id":215538916354}||


```

Queste forze che mantengono l'equilibrio si chiamano forze interne della trave.

![[Azione assiale]]

### Lavorare con le masse
$$
\overline{F}=m\overline{a}
$$
```math
||{"id":419547970101}||


```


$$
d\overline{F}_{p} = dm\overline{a}
$$
$$
\begin{align}
\text{Equilibrio in y} & \implies \int_{A} d\overline{F}_{py} \,  = \int_{A} h\rho\overline{a} \, dA =\sum_{j}F_{yj}=0 \\
\text{Equilibrio in x} & \implies \int_{A} d\overline{F}_{py} \,  = \int_{A} h\rho\overline{a} \, dA =M\overline{a} =F_{tot} \\
\text{Equilibrio dei M}  & \implies \int_{A}(y_{1}\overline{j})\land dF_{px}\overline{i}  \,=-\overline{k}\int_{A}y_{1}h\rho a  \, dA =0 \\
\text{Baricentro} & \implies \tilde{y}=\frac{1}{A}\int _{A}y \, da = y_{G} = \frac{h\rho}{M}\int _{A}y \, dA    
\end{align}
$$
$$
y_{G} = \frac{1}{M}\int _{V}\rho(x,y,z) \, dV 
$$

```math
||{"id":1500801384444}||


```
$$
\begin{align}
\overline{a}_{P} &  =\dot{\overline{\omega}}-\omega^{2}(P-O) \\
d\overline{F_{P}} & =dm\overline{a}_{P}=dAh\rho \overline{a}_{P} \\
d\overline{C}_{O} & =(P-O)\land d\overline{F}_{P}=(P-O)\land \overline{a}_{P}(dAh\rho)=\dot{\omega}(PO)^{2}(dAh\rho)
\end{align}
$$
$$
\begin{align}
\overline{C}_{O} &  = h\rho \overline{\dot{\omega}}\int_{A} (PO)^{2} \, dA=h\rho\overline{\dot{\omega}}\int_{A} (x_{G}^{2}+y^{2}_{G}) + (x_{1}^{2}+y^{2}_{1})+2(x_{1}x_{G} + y_{1}y_{G}) \, dA   \\
 & = Mr^{2}\overline{\dot{\omega}} +J_{G}\overline{\dot{\omega}} \\
J & =Mr^{2} = J_{O}\overline{\dot{\omega}} \\
\frac{J_{G}}{M} & = \varrho
\end{align}
$$

Dove la $r$ cambia rispetto a quello che sto calcolando, la $r$ di $J_{G}$ è $(G-O)$ invece l'altra è $(P-G)$

Le forze ed i momenti si possono sommare.

```math
||{"id":644889132490}||


```

$$
\begin{cases}
F_{1x}+F_{2x} = R_{x} \\
F_{1y}+F_{2y} = R_{y} \\
F_{2x}b-F_{1x}a = M 

\end{cases}
$$

>[!tip] 
>Notare che in queste relazioni non è importante se le masse siano collegate o meno
