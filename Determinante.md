---
tags: [gal]
---
Questo è il fattore per quanto si scala lo spazio che viene moltiplicato con la matrice da cui viene calcolato.

Questo si calcola con i triangoli di sarrus per le 3x3 o con lo sviluppo di lapace per le altre

$$
\det A = \sum_{j=1}^{n}a_{ij}A_{ij}
$$
dove $A_{ij}$ è il complemento algebrico

![[Complemento algebrico]]

### Proprietà

Il determinante gode di:
	• Normalizzazione => $\det I=1$
	• Simmetria => $\det A=\det A^{t}$
	• Formula di binet => $\det AB=\det A\det B$
	• $\det A^{-1}=\frac{1}{\det A}$
	• Alternanza => se scambio 2 righe $\det A=-\det A'$
	• Multilinearità => se moltiplico una riga per uno scalare $\det A=t\det A'$
	• Se una riga è la somma di 2 vettori => $\det A=\det A'+\det A''$
	• Se 2 linee non sono indipendenti => $\det A=0$
