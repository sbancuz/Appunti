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


### Funzione analitica

Sia $f:(a,b)\subseteq \mathbb R \to \mathbb R$ derivabile infinite volte in $x_{0}\in(a,b)$ si dice che $f$ è una funzione analitica in $x_{0}$ se la [[Serie di Taylor]] con centro $x_{0}$ ha raggio di convergenza $R\in (0,\infty)\cup\{\infty\}$ e inoltre $\exists {R_{1}} \in {(0,R]}$ tale che 
$$
f(x) = \sum \frac{f^{(n)}(x_{0})}{n!}(x-x_{0})^{n}
$$

=> [[Serie di potenze]]

### Funzione regolare a tratti

Sia $f:[a,b]\to \mathbb{R}$, diciamo che $f$ è regolare a tratti in $[a,b]$ se esiste un numero finito di punti $a=x_{1}<x_{2}<\dots<x_{n}=b$ ovvero una partizione di $[a,b]$ tale che:
1) $f$ è continua in $(x_{i},x_{i+1}), \forall {i} =1,\dots ,n-1 {}$  ed esistano finiti i limiti $\lim_{ x \to x_{i}^{+} } {f(x)}$ e $\lim_{ x \to x_{i}^{-} } f(x){}$
2) $f$ è derivabile in $(x_{i},x_{i+1}), \forall {i} =1,\dots ,n-1 {}$  ed esistono finiti i limiti $\lim_{ x \to x_{i}^{+} } {f'(x)}$ e $\lim_{ x \to x_{i}^{-} } f'(x){}$

 