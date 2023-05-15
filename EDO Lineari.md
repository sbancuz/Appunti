---
tags: [analisi_2]
---

Una EDO del primo rodine è lineare se è della forma 
$$
y'(t) = a(t) y(t) +b(t)
$$
dove $a,b:I  \subseteq \mathbb R \to \mathbb R$, inoltre se $b=0$ l'equazione si dice omogenea, altrimenti completa.

>[!info]
>$a,b$ non è detto che siano lineari

>[!info]
>Le EDO lineari sono già in forma normale

### Teorema) Formula risolutiva per le EDO del primo ordine lineari

Date $a,b$ continue su $I$, l'integrale generale della EDO è dato dalla formula
$$
y(t) = e^{A(t)}[B(t) + c], t \in I
$$
dove $c\in \mathbb R$, $A$ è la primitiva di $\int  a\,$, e $B$ è una qualunque primitiva di $\int b \, e^{-A}$

#### Dimostrazione

Svolgiamo 3 passi:
- Passo 1) Porto a sinistra il termine con la $a$ e moltiplico per $e^{-A}$ => $(ye^{-A})' = y'e^{-A}-aye^{-A} = be^{-A}$
- Passo 2) Applico il (TFCI) troviamo la primitiva su entrambi i membri
$$
ye^{-A} = \int(ye^{-A})'  \, dt = \int  be^{-A} \, dt + c 
$$
 - Passo 3) Moltiplico per $e^{A}$ e ottengo 
 $$
y(t) =e ^{A(t)}\left[ \int be^{-A(t)} \, dt +c  \right]
$$

### Proprietà

- Le EDO lineari del primo ordine soddisfano il [[Principio di sovrapposizione]]