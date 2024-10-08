---
tags: analisi_2
---
Data $A: I\subseteq \mathbb R\to \mathbb M_{n \times x}$ e $\underline{b}:I\to \mathbb R^{n}$ continue, l'integrale generale del sistema completo $\underline{y}'(t)=A(t)\underline{y}(t)+\underline{b}(t)$ è
$$
\underline{y}(t) = \underline{y}_{\sigma}(t)+\underline{y}_{\phi}(t)
$$
dove $\underline{y}_{\sigma}(t)$ è l'integrale generale del SDL omogeneo ($\underline{y}'(t)=A(t)\underline{y}(t)$) e $\underline{y}_{\phi}(t)$ è una soluzione particolare del sistema completo.

>[!note]
>Si possono quindi utilizzare i metodi di risoluzione visti per i [[Sistemi lineari omogenei]] per l'integrale generale e al metodo di somiglianza per la soluzione particolare

### Metodo di somiglianza per sistemi lineari non omogenei

Dopo aver trovato l'integrale generale dato dal sistema lineare omogeneo associato ci rimane da trovare $\underline{y}_{\phi}$, quindi cerco $a,b,c,d\in \mathbb R$ tali che
$$
\underline{y}_{\phi} = \left( \begin{matrix}
ae^{x}+b \\
ce^{x}+d
\end{matrix} \right), 
\underline{y}_{\phi}' = \left( \begin{matrix}
ae^{x} \\
ce^{x}
\end{matrix} \right) 
$$
sia soluzione del sistema
$$
\underline{y}'_{\phi}(x) = A\underline{y}_{\phi}(x) + \underline{b}(x)
$$
### Altro metodo per ottenere l'integrale particolare

Dato un sfs, l'integrale generale nel caso omogeneo è dato da 
$$
\underline{y}_{\sigma}(x) = W(x)\underline{c}
$$
dove la W è la matrice Wroskiana relativa al sfs e $c$ un vettore di costanti.
Possiamo generalizzare questa formula al caso non omogeneo utilizzando il fatto che la $W$ è invertibile
$$
\underline{y}(x) = W(x) \left( \int [W(s)]^{-1}\underline{b}(s) \, ds +\underline{c} \right)
$$
>[!tip]
>La primitiva di un vettore di funzioni integrabili è il vettore delle primitive delle funzioni

In particolare, nel caso A sia diagonale avremo che 
$$
\underline{y}_{\sigma}(x) = e^{Ax}\underline{c}'
$$
con $\underline{c}'$ un'altro vettore di costanti, con questo otteniamo che
$$
W(x) = c_{0}e^{Ax}
$$
dove $c_{0}\in \mathbb R$ e mettendo tutto assieme
$$
\underline{y}(x) = e^{Ax}\left(  \int e^{-As} \underline{b}(s) \, ds + \underline{c}  \right)
$$
>[!nota]
>Questa è una generalizzazione della formula risolutiva per le EDO del primo ordine lineari



