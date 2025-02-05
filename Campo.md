---
tags:
  - analisi_1
  - logica_algebra
---
Un [[anello]] commutativo privo di zero-divisori non nulli è detto **dominio di integrità**. Se invece tutti gli elementi non nulli sono invertibili, allora è detto **campo**.

>[!example]
>L'anello $\mathbb{Z}$ è un dominio di integrità, ma non è un campo. Gli anelli $\mathbb Q, \mathbb{R}, \mathbb{C}$ sono campi.

Possiamo anche vedere che $\mathbb{Z}_{n}$ è un campo sse $n\in \mathbb{N} \setminus\{ 0,1 \}$ è un **numero primo**. Infatti un [[Ideale]] di $\mathbb{Z}_{n}$ è un sottogruppo di $\mathbb{Z}_{n}$. Poiché $\mathbb{Z}_{n}$ è [[Gruppo#Gruppo ciclico]], i suoi sottogruppi sono ciclici e sono $\{ \left< [m] \right> : [m]\in \mathbb{Z}_{n} \}$. Inoltre $\left< [m] \right> \subseteq Z_{n}$ è un ideale. Inoltre se $n>1$
$$
\{ \left< [m] \right> : [m]\in \mathbb{Z}_{n} \} = \{  \{ [0] \}, \mathbb{Z}_{n} \} \cup \{ \left< [m] \right> : MCD_{m\neq 0}\{ m,n \}\neq 1 \}
$$
Quindi $\mathbb{Z}_{n}$ è un campo sse $n$ è un numero primo.

Sia $A$ un campo e sia $\left< 1_{A} \right>$ il sottogruppo di $(A, +)$ generato da $1_{A}$ generato da $1_{A}$. L'intersezione di tutti i sottocampi di $A$ contenenti $\left< 1_{A} \right>$ si chiama **sottocampo fondamentale di $A$**. Se $p \in \mathbb{N}$ è un numero primo, il sottocampo fondamentale di $\mathbb F$è $\mathbb F_{p}$ perché $\left< [1] \right> = \mathbb F_{p}$.

Per calcolare il MCD basta usare l'algoritmo di **Euclide**
```pseudo
\begin{algorithm}
\begin{algorithmic}
\Procedure{Euclide}{$a, b$}
    \While{$b \neq 0$}
        \State $r \gets a \mod b$ \Comment{Calcola il resto}
        \State $a \gets b$ \Comment{Aggiorna $a$ con il valore di $b$}
        \State $b \gets r$ \Comment{Aggiorna $b$ con il valore di $r$}
    \EndWhile
    \Return $a$ \Comment{Il massimo comune divisore è $a$}
\EndProcedure
\end{algorithmic}
\end{algorithm}
```
Un'identità del tipo
$$
ax +by =MCD\{ a,b \}
$$
si chiama **identità di Bézout**. Per trovare $x,y$ basta calcolare il MCD e computare i valori all'inverso.

[Teorema]
Siano $a,b\in \mathbb{N}\setminus \{ 0 \}$. Se $a|b$, allora $a = MCD \{ a,b \}$. Se $a \cancel{ | } b$, e $r$ è l'ultimo resto non nullo nell'algoritmo di Euclide per $a, b$, allora $r=MCD\{ a,b \}$. Inoltre esistono $x,y \in \mathbb{Z}$ tali che 
$$
ax + by = MCD\{ a,b \}
$$
### Equazione Diofantea lineare

Un'equazione del tipo 
$$
ax + by = c \quad a,b,c \in \mathbb{Z}
$$
è definita come **equazione Diofantea lineare**.

[Teorema]
Siano $a,b,c\in\mathbb{Z}$. Allora esistono $x,y\in\mathbb{Z}$ tali che $ax+by = c$ sse $MCD\{ a,b \}$ divide $c$.

>[!note]- Dimostrazione
>Se $ax + by = c$ allora $MCD\{ a,b \}$ divide $c$. 
>Se $d = MCD\{ a,b \}$, allora abbiamo un identità di Bézout $ax,by = d$. Se $d | c$, ossia ho che $c = kd$,$k\in \mathbb{Z}$ si ha che $a(kx) + b(ky) = kd =c$

Se $p\in\mathbb{N}$ è un numero primo, scriviamo che $\mathbb F_{p} = \mathbb{Z}_{p}$; il campo $\mathbb F_{p}$ ha $p$ elementi. 


