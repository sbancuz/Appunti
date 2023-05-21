---
tags: analisi_2,wroskiano
---
### Teo della struttura dell'integrale generale dei sistemi omogenei

Sia $A:I\subseteq \mathbb R \to M_{n\times n}$ continua. L'integrale generale di $\underline{y}'(x) = A(x)\underline{y}(x)$ è uno [[Spazio vettoriale]] di dimensione n, cioè si può scrivere come 
$$
\underline{y}_{\sigma}=c_{1}\underline{y}_{\sigma,1}(x)+\dots+\underline{y}_{\sigma,n}(x)
$$
con $\underline{c} in \mathbb R^{n}$ dove $\underline{y}_{\sigma}$ sono soluzioni linearmente indipendenti. In particolare $y_{\sigma}$ sono una [[Base del sistema]] dello spazio delle soluzioni e vengono chiamate sistema fondamentale di soluzioni. (sfs)

Per verificare l'indipendenza lineare di n soluzioni basta considerare le combinazioni lineari che si annullano in $x_{0}\in I$

### Matrice Wroskiana 

Date n funzioni $\underline{y}_{i}: J\subseteq \mathbb R\to \mathbb R^{n}$ chiamiamo Wroskiana la matrice costruita affiancando i vettori colonna $y_{i}(x)$ cioè
$$
W(x) = (\underline{y}_{1}(x)|\dots|\underline{y}_{n}(x))
$$
e chiamiamo determinante Wroskiano il suo determinante,

### Determinante Wroskiano

Date n funzioni $\underline{y}_{i}: J\subseteq \mathbb R\to \mathbb R^{n}$ di
$$
\underline{y}'(x) = A(x)\underline{y}(x)
$$
se $\exists {x_{0}} \in {J}$ tale che $\det W(x_{0})\neq 0$ allora $\underline{y}_{\sigma,1}(x),\dots,\underline{y}_{\sigma,n}(x)$ sono linearmente indipendenti e quindi formano un sfs e l'integrale generale si può scrivere nella forma
$$
W(x)\underline{c}
$$
dove $\underline{c}=(c_{1},\dots,c_{n}) \in \mathbb R^{n}$ che si chiama il vettore generico in $\mathbb R^{n}$. Inoltre la soluzione del problema di Cauchy associato con la condizione $\underline{y}(x_{0}) = \underline{y}_{0}$ è $\underline{y}(x)=W(x)W^{-1}(x_{0})\underline{y}_{0}$ 

### Risoluzione esplicita con A(x) costante

Rimane il problema di trovare n soluzioni linearmente indipendenti. Lo trattiamo in 2 casi:
- Con $A(x)$ costante [[Diagonalizzabile]] in $\mathbb R$
- Con $A(x)$ con 2 autovalori complessi coniugati

### Teorema integrale generale per un sistema differenziale lineare omogeneo con A diagonalizzablie 

Data $A\in \mathbb M_{2\times2}$ diagonale, un sfs per $\underline{y}'(x)=A\underline{y}(x)$ con $x\in \mathbb R$ è $\underline{y}_{\sigma,1}(x)=e^{\lambda_{1}x}\underline{v}_{1},\dots,\underline{y}_{\sigma,n}(x)=e^{\lambda_{n}x}\underline{v }_{n},$ dove $v_{1},\dots ,v_{n}$ sono autovettori linearmente indipendenti relativi agli autovalori $\lambda_{1},\dots,\lambda _n$
$$
\underline{y}_{\sigma}=\sum_{i=1}^{n}c_{i}e^{\lambda_{i}x}\underline{v}_{i}
$$
