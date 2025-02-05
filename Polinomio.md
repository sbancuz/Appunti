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

>[!example]
>Gli elementi di $\mathbb F_{4} = \mathbb F_{2} /\left< 1 + x + x^{2} \right>$ sono $\{ 0, 1, x, 1 + x\}$. In particolare abbiamo che $[1 + x + x^{2}] = [0] \implies [x^{2}] = -[x+ 1] = [-x-1] = [x + 1]$
>
>Per tutti i calcoli bisogna chiaramente lavorare in $\mathbb F_{2}$ visto che è il campo che stiamo dividendo.

[Teorema - Teorema di Ruffini]
Sia $f(x)\in K[X]$ un polinomio non nullo. Se $\alpha\in K$, il resto della divisione di $f(x)$ per $x - \alpha$ è $f(\alpha)$. In particolare, $\alpha$ è radice di $f(x)$ sse $x - \alpha$ divide $f(x)$ in $K[X]$.

>[!note]- Dimostrazione
>$f(x)= (x-\alpha)g(x) + r(x)$ con $r(x) = 0$ oppure $deg(r(x)) < 1$. Quindi $r(x)$ è un polinomio constante $r(x) = c\in K$. Calcolando un $\alpha$ si ottiene $f(\alpha) = c$ 

[Proposizione]

Se $K$ è un campo, ogni sottogruppo finito del gruppo moltiplicativo $K \setminus \{  0 \}$ è ciclico. In particolare, se $k$ è un campo finito, $K \setminus \{ 0 \}$ è un gruppo ciclico.

Sia $p \in \mathbb{N}$ un numero primo e sia $n \in \mathbb{N}\setminus \{  0\}$. Sia $Q(x)\in \mathbb F_{p}[X]$ un qualsiasi polinomio irriducibile di grado $n$. Definiamo il campo
$$
\mathbb F_{p^{n}} = \mathbb F_{p}[x] / \left< Q(X) \right> 
$$
Vogliamo adesso dimostrare che se $Q(X),Q'(X)\in \mathbb{F}_{p}[X]$ sono polinomi irriducibili di gruppo $n$, allora
$$
\mathbb{F}_{p}[X]/\left< Q(X) \right> \simeq \mathbb{F}_{p}[X] / \left< Q'(X) \right>  
$$
quindi la definizione di $\mathbb{F}_{p^{n}}$ è ben posta, a meno di isomorfismi.

Sia $F\subseteq K$ un ampliamento di campi e sia $\alpha\in K$. Il più piccolo sottocampo generato da $F, \alpha$ si chiama **l'ampliamento di $F$ in $K$ generato da $\alpha$**, e si indica con $F(\alpha)$. Un tale ampliamento si dice **semplice** poiché generato da un solo elemento.

Siano $F\subseteq K$ due campi. Un elemento $\alpha\in K$ si dice **algebrico** su $F$ se è radice di qualche polinomio non nullo su $f(x)\in F[X]$. Altrimenti si dice **trascendente**. Dato un ampliamento di campi $F \subseteq K$ e $\alpha \in K$, si consideri il morfismo di anelli
$$
\begin{align}
v_{\alpha} :  & F[X] \to K \\
 & f(x) \to f(\alpha)
\end{align}
$$
$Ker(v_{\alpha})$ è l'ideale di $F[X]$ costituito dai polinomi che si annullano in $\alpha$. Quindi $\alpha$ è algebrico su $F$ sse $Ker(v_{\alpha})$ è un ideale non nullo di $F[X]$ poiché è ad ideali principali, $Ker(v_{\alpha}) = \left< m(x) \right>$ dove $m(x)$ è l'unico polinomio monico in $Ker(v_{\alpha})$.

Se $\alpha \in K$ è algebrico su $F$, il polinomio $m(x)$ definito sopra si chiama **polinomio minimo** di $\alpha$ su $F$ sse $m(x)$ è monico e irriducibile. Se $deg(m(x))=n$, $\alpha$ si dice algebrico di grado $n$.

[Proposizione]
Sia $F\subseteq K$ un ampliamento di campi e $\alpha\in K$. Si consideri il [[Morfismo]] di [[Anello|Anelli]] $v_{\alpha}: F[X] \to K$ allora $Im(v_{\alpha})$ è il più piccolo sottoanello di $K$ contente sia $F$ che $\alpha$.

[Corollario]
Sia $F \subseteq K$ un ampliamento di campi e sia $\alpha \in K$. Allora
$$
F(\alpha) = \{ f(\alpha)g(\alpha)^{-1} : f(x),g(x) \in F[X], g(\alpha) \neq 0 \}
$$
>[!note]- Dimostrazione
>Il più piccolo sottoanello di $K$ contenente sia $F$ che $\alpha$è
>$$
>Im(v_{\alpha}) = \{ f(\alpha) : f(x) \in F[X]\} 
>$$
>che prendendo gli inversi in $K$ si ottiene la tesi.

Se $\alpha$ è algebrico su $F$, si ha che $Im(v_{\alpha}) \simeq F[X] / \left< m(x) \right>$ dove $m(x)$ è il polinomio minimo di $\alpha$. Quindi $Im(v_{\alpha})$ è un campo. Se $n$ è il grado di $\alpha$, si ha che
$$
F(\alpha) = \{ c_{0} + c_{1}\alpha + \dots + c_{n- 1}\alpha^{n-1} : c_{i} \in F \}
$$
>[!example]
>Si consideri l'ampliamento $\mathbb{Q} \subseteq \mathbb{R}$. L'elemento $\sqrt{ 2 }\in \mathbb{R} \setminus \mathbb{Q}$ è algebrico su $\mathbb{Q}$, con polinomio minimo $x^{2} - 2$. Quindi $\sqrt{ 2 }$ ha grado $2$ su $\mathbb{Q}$ e 
>$$
>\mathbb{Q}(\sqrt{ 2 }) = \{ c_{0} + c_{1}\sqrt{ 2 } : c_{0},c_{1} \in \mathbb{Q} \}
>$$

Adesso possiamo mostrare che il campo $\mathbb{F}_{p^{n}}$ è un ampliamento semplice del campo $\mathbb{F}_{p}$

[Proposizione]
Sia $\alpha \in \mathbb{F}_{p^{n}}$ un generatore del gruppo moltiplicativo $\mathbb{F}_{p^{n}}\setminus \{ 0 \}$ allora $\mathbb{F}_{p^{n}} = \mathbb{F}_{p}(\alpha)$

>[!note]- Dimostrazione
>$\mathbb{F}_{p^{}}(\alpha)$ è il più piccolo sottocampo di $\mathbb{F}_{p^{n}}$ contenente sia $\mathbb{F}_{p^{}}$ che $\alpha$. Quindi $\mathbb{F}_{p^{}}(\alpha) \subseteq \mathbb{F}_{p^{n}}$. Poiché $\alpha$ genera il gruppo moltiplicativo $\mathbb{F}_{p^{n}}\setminus \{ 0 \}$, si ha che $\mathbb{F}_{p^{n}} \subseteq \mathbb{F}_{p^{}}(\alpha)$

