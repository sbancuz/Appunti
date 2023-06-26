---
tags: [meccanica]
---

### Senza strisciamento

```math
||{"id":419741315122}||


```
$$
\overline{V_{P}} = \overline{\omega}\land(P-A)
$$

Quando non c'è strisciamento non c'è neanche l'attrito visto che $\overline{v_{a}} = 0$

```math
||{"id":416703588309}||


```
$$
\begin{align}
\overline{V_{C}} =  & -\omega R\overline{i} =\dot{x}\overline{i}\\
\overline{V_{D}} =  & \omega R\overline{j} - \omega R\overline{i} \\
\overline{a_{D}} =  & -\omega ^{2}R\overline{i}\\
x= & -R\theta \\
\dot{x} =  & -R\omega
\end{align}
$$

Per ipotesi si ha $\omega = cost \to \overline{a_{C}}=0$

### Attrito volvente
```math
||{"id":224164428547}||


```
$$
|\overrightarrow{T}| \leq f_{s}|\overrightarrow{N}|
$$
>[!warning]
L'attrito è sempre in verso opposto alla velocità con cui il corpo si muove
$$
\overrightarrow{T} = -f_{d}|\overrightarrow{N}|\frac{\overrightarrow{V}_{rel}}{|\overrightarrow{V}_{rel}|}
$$

Se il rotolamento è ideale gli attriti non contano, ma quindi in condizioni non ideali cosa succede?

Prendi una superficie di gomma e una di legno, il disco si fermerà molto prima su quella di gomma. Questo è dato dalla deformazione elastica dei materiali.

```math
||{"id":317847168507}||


```
Il valore della deformazione è l'integrale della compressione, come si vede in condizioni ideali $\int P \, d\epsilon = 0$ essendo pari, ma in condizioni anaelastiche no e quindi consuma energia.
```math
||{"id":213563903273}||


```
$$
\int _{1}^{5}P \, d\epsilon = \left[ \frac{N \times m}{m^{3}} \right]
$$
```math
||{"id":1220657150552}||


```
$$
\begin{align}
 & |\overrightarrow{M}_{R}| = |\overrightarrow{N}| f_{v}R \\
 & \overrightarrow{M}_{R} = - |\overrightarrow{N}|f_{v}R \frac{\overrightarrow{\omega}}{|\overrightarrow{\omega}|}  \\
 & W_{R} = \overrightarrow{\omega} \times \overrightarrow{M}_{R} = -|\overrightarrow{N}|f_{v}R |\overrightarrow{ \omega}|
\end{align}
$$

