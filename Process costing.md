---
tags: [economia]
---

Tutte le tipologie di costo sono allocate utilizzando un criterio di tipo proporzionale.

Questo viene usato per le produzioni omogenee con processi di tipo a flusso che esistono sotto una serie di ipotesi di base:
	• Produzioni mono-reparto
	• Produzionibegin mono-prodotto

$$
CPI_{unitario}=\frac{CPI}{Q}
$$
### Schema del processo

Sia le unità completate che quelle in lavorazione devone essere espresse in termini di un unica unità di misura, detta [[Unità Equivalente]], che poi viene usata per determinare il costo.

$$
UE = UE_{pf} + U_{WIPfin}\times a_{fin}
$$
Facendo si che 
$$
\begin{align}
CPI_{unitario}  & = \frac{CPI}{UE} = CPI_{unitarioPF} \\
CPI_{unitarioWIPfin}  & = CPI_{unitario}\times WIP_{fin}\times a_{fin}
\end{align}
$$

![[Schema di processo.png]]

In presenza anche dei semilavorati iniziali si ha che
$$
C_{WIPiniziale}+CA = C_{PF}+C_{WIPfinale}
$$
Dove $CA$ sono i costi aggiuntivi dati da:
	• $CC$ => costi di conversione (Eg: manodopera)
	• $CMP$ => costi delle materie prime

### Costo medio vs FIFO

Nella logica del **costo medio** calcolando i $CPI$ considero anche i costi del $WIP$ iniziale.

Invece nella logica **FIFO** si considerano solamente le unità equivalenti che hanno assorbito i costi totali sostenuti del periodo considerato

|-|FIFO|Costo medio|
|----|----|-----|
|Principio|Per determinare il costo unitario relativo a un periodo t, il costo di produzione deve far riferimento ai costi effettivamente sostenuti per produrre le unità completate (QC)* e WIP finale, mentre vengono trascurati i costi relativi a WIP iniziale|Per determinare il costo unitario, relativo a un periodo t, si considerano unità completate e WIP finale, incorporando anche i costi delle WIP iniziale|
|Output|$UE=Q_{c}+WIP_{f}\times a_{f} - WIP_{i}\times a_{i}$|$UE=Q_{c}+WIP_{f}\times a_{f}$|
|Costo totale|$CA$|$CA+CI$|
|Costo UE|$\frac{CA}{UE}$|$\frac{CA+CI}{UE}$|
|Costo $WIP_{f}$|$C_{UE}\times WIP_{f}\times a_{f}$| $C_{UE}\times WIP_{f}\times a_{f}$|
|Costo complessivo|$C_{Q_{c}}=CA-C_{WIP_{f}}+CI$|$C_{Q_{c}}=C_{UE}\times Q_{c}$|

Dove $CI$ sono i costi incorporati

In presenz di più prodotti è necessario usare il coefficiente di equivalenza

### Passi del process costing

Per mette in atto il process costing bisogna:
	• Individuare un Prodotto 
	• Calcolare l'output in termini di [[Unità Equivalente]]
	• Calcolare i costi totali da dare ai prodotti
	• Calcolare il costo per unità equivalente
	• Allocare i costi alle unità di prodotto finito e [[WIP]]
