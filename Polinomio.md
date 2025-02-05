---
tags:
  - logica_algebra
---
Sia $k$ un [[Campo]]. Una [[Funzioni|Funzione]] $f: \mathbb{N} \to K$ è detta **successione a valori** in $K$. Ad una successione a valori in $K$ corrisponde una serie formale nell'indeterminata $X$ su $K$
$$
\sum f(n) X^{n}
$$
Se l'insieme $\{ n \in \mathbb{N} : f(n) \neq 0 \}$ è finito, diciamo che la serie formale $\sum f(n)X^{n}$ è un **polinomio** $p$ nell'indeterminata $X$ di grado
$$
deg(p) = \max\{ n\in \mathbb{N} : f(n) \neq 0 \}
$$
Il grado del polinomio $0$ non è definito. L'insieme dei polinomi nell'indeterminata $X$ a coefficienti in $k$ lo indichiamo $K[X]$. Esso ha una struttura di [[Anello]] commutativo con le seguenti operazioni
- $P + Q = \sum(a_{n} + b_n)X^{n}$
- $PQ = \sum(\sum_{i}^{n}a_{i}b_{n-i})X^{n}$

L'unità dell'anello $K[X]$ è il polinomio $1_{K}$

[Proposizione]
Siano $P,Q\in K[X]$ polinomi non nulli, allora
$$
deg(PQ) = deg(P)+ deg(Q)
$$
in particolare, $K[X]$ è un dominio di integrità.

Un polinomio si dice **monico** se il coefficiente del termine di grado massimo è uguale a $1$. Sia $K$ un campo, un polinomio $p$ si dice **irriducibile** se gli unici suoi divisori sono del tipo $a,ap$, con $a\in K \setminus \{ 0 \}$, altrimenti si dice **riducibile**.

>[!note]
>Ogni polinomio di grado $1$ è irriducibile

Sia $\alpha\in K$, esso si dice **radice** del polinomio $p = \sum_{n}^{deg(p) }a_{n}x^{n} \in K[X]$ se $\sum_{n}^{deg(p) }a_{n}\alpha^{n} = 0$. Anche nell'anello $K[X]$, come in $\mathbb{Z}$, abbiamo un algoritmo di divisione euclidea. Siamo $f(x), g(x)$ polinomi non nulli, allora esistono unici polinomi $q(x),r(x)$ tali che
$$
f(x) = g(x)q(x) + r(x) \quad r(x) = 0 \lor deg(r(x)) < deg(p(x))
$$
$q(x)$ si chiama **quoziente** e $r(x)$ **resto** della divisione.

[Teorema]
L'anello $K[X]$ è a ideali principali. Se $I = \left< p(x) \right>$ allora esiste un unico generatore monico di $I$.

Definiamo il $MCD$ tra due polinomi $f,g\in K[X]$ come l'unico massimo comun divisore monico. Come in $\mathbb{Z}$, il MCD si può trovare con l'algoritmo delle divisioni successive, che ci da anche un'identità di Bézout.

[Proposizione]
Sia $K$ un campo e $p(x)\in K[X]$ un polinomio irriducibile. Allora l'anello quoziente $K[X] /\left< p(x) \right>$ è un campo.

>[!note]- Dimostrazione
>Sia $[f] \in K[X] /\left< p(x) \right>$ tale che $[p]\neq[0]$, ossia $p(x)$ non divide $f(x)$. Dunque $MCD\{ f(x), g(x) \} = 1$ perché $p(x)$ è irriducibile. Quindi abbiamo questa identità di Bézout.
>$$
>a(x)f(x) + b(x)p(x) = 1
>$$
>in $K[X] / \left< p(x) \right>$

