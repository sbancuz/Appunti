---
tags: [analisi_1]
---
![[Teorema degli zeri]]

![[Teorema di Weierstrass]]

![[Teorema dei valori intermedi]]

## Inversa di una funzione continua

Sia $f:I\to R$ con $I$ intervallo qualunque continua in $I$, allora $f$ è invertibile sse $f$ è strettamente monotona, inoltre anche $f^{-1}$ è strettamente monotona e continua

>[!note]- Dimostrazione
>Abbiamo già visto che se $f$ è strettamente monotona, allora è invertibile
>
>Allora sia $f$ continua e invertibile, proviamo che sia monotona
>
>Per assurdo, non sia strettamente monotona, quindi $\exists {x_{1},x_{2},x_{3}} \in {I}$ tali che $x_{1}<x_{2}<x_{3}$ ma $f(x_{1})<f(x_{2})$ e $f(x_{2})>f(x_{3})$ o $f(x_{1})>f(x_{2})$ e $f(x_{2})<f(x_{3})$
>
>Per il teorema dei valori intermedi $\exists {x_{0}} \in {(x_{1},x_{2})}$ tale che $f(x_{0})=f(x_{3})$, ma $x_{0}\neq x_{3}$ che è assurdo perché $f$ è invertibile e quindi iniettiva
>
>Resta da vedere se anche $f^{-1}$ è continua
>
>Ma, se $f$ è strettamente monotona, sappiamo già che $f^{-1}$ è strettamente monotona, quindi per il teorema di monotonia o è continua o ha discontinuità a salto.
>
>Ma se ha discontinuità a salto, la sua immagine non è un intervallo, assurdo poiché l'immagine di $f^{-1}$ è $I$

