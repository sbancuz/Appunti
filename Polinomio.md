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

Siano $p(x), q(x) \in \mathbb{F}_{p}[X]$ due polinomi irriducibili di grado $n$, vogliamo costruire un isomorfismo.
$$
f: \mathbb{F}_{p}[X] /\left< p(x) \right> \to \mathbb{F}_{p}[X] / \left< q(x) \right> 
$$
Per farlo abbiamo abbiamo bisogno di questo risultato. Siano $F\subseteq K,K'$ due ampliamenti di campi. Se $\alpha \in K$ è algebrico di grado $n$ su $F$ con polinomio minimo $m(x)$, esiste un morfismo di campi $\phi:\mathbb{F}(\alpha) \to K'$ che fissa $F$ sse $m(x)$ ha una radice in $K'$. In questo caso i morfismi $\phi$ sono tanti quanti le radici distinte $\beta_{1},\dots,\beta_{s}$ di $m(x)$ in $K'$ e sono tutti e soli quelli definiti da
$$
c_{0} + c_{1} \alpha + \dots + c_{n-1}\alpha^{n-1} \to c_{0} + c_{1}\beta + \dots + c_{n-1}\beta^{n-1}
$$
>[!note]- Dimostrazione
>Se $\alpha$ è algebrico di grado $n$ su $F$, con polinomio minimo $m(x)$ e $\phi: F(\alpha) \to K'$ è un morfismo, allora
>$$
> 0 = \phi(0) = \phi(m(\alpha)) = m(\phi(\alpha))
>$$
>quindi $\phi(\alpha)$ deve essere radice di $m(x)$ in $K'$. Viceversa, sia $\beta$ una radice di $m(x)$ in $K'$ e considerando il morfismo di anelli $v_{\beta}: F[X] \to K'$. Poiché $m(x)\in Ker(v_{\beta})$, dal teorema di isomorfismo per anelli abbiamo che $Ker(v_{\beta}) = \left< (m(x)) \right>$, essendo $m(x)$ irriducibile. Quindi abbiamo trovato un morfismo iniettivo $\phi:F(\alpha) \to K'$ che soddisfa le proprietà dell'enunciato della proposizione.

Sia $F$ un [[Campo]] e $f(x) \in F[X]$ un polinomio di grado $n \geq 1$. Un campo $K$, ampliamento di $F$, si dice **campo di spezzamento** di $f(x)$ su $F$ se $f(x)$ fattorizza in polinomi di grado $1$ su $K[X]$ e non ci sono campi intermedi con questa proprietà

>[!example]
>$\mathbb{Q}(\sqrt{ 2 })$ è un campo di spezzamento di $x^{2} - 2 \in \mathbb{Q}[X]$. $\mathbb{C}$ è campo di spezzamento di $x^{2} + 1 \in \mathbb{R}[X]$

Adesso vogliamo mostrare che un campo che ha cardinalità $p^{n}$ è un campo di spezzamento del polinomio
$$
x^{p^{n}} - x \in \mathbb{F}_{p}[X]
$$
infatti, se $K$ è un campo e $|K| = p^{n}$, allora il suo gruppo moltiplicativo $K \setminus \{ 0 \}$ ha cardinalità $p^{n} - 1$ e quindi si ha $\alpha^{p^{n}- 1}=1$ in quanto $K \setminus \{ 0 \}$ è ciclico. Quindi ogni elemento di $K$ è radice del polinomio $x^{p^{n}}-x$. Per il teorema di Ruffini, $K$ è un campo  di spezzamento.

Adesso manca solo da dimostrare che ogni polinomio di grado $n$ irriducibile in $\mathbb{F}_{p}[X]$ divide $x^{p^{n}} - x \in \mathbb{F}_{p}[X]$. Tutti e soli i polinomi irriducibili su $\mathbb{F}_{p}$ di grado $n$ sono i fattori irriducibili di grado $n$ di $x^{p^{n}} - x \in \mathbb{F}_{p}[X]$

>[!Dimostrazione]-
>Sia $p(x) \in \mathbb{F}_{p}[X]$ irriducibile di grado $n$ e sia $K = \mathbb{F}_{p}[Y] / \left< p(y) \right>$, allora $K$ ha $p^{n}$ elementi che sono le radici di $x^{p^{n}} - x$. Poiché $y \in K$ è una radice, allora $p(x)\in K[X]$ e $p(x), x^{p^{n}} - x \in \mathbb{F}_{p}[X]$ hanno una radice in comune in $K\implies$ per il teorema di Ruffini hanno un fattore in comune $x-y\in K[X]$. Quindi poiché il MCD in $\mathbb{F}_{p}[X]$ è lo stesso che in $K[X]$, allora $p(x), x^{p^{n}} - x \in \mathbb{F}_{p}[X]$ hanno un MCD diverso da $1\in \mathbb{F}_{p}[X]$. Visto che $p(x)$ è irriducibile allora $p(x)$ divide $x^{p^{n}} - x$

Adesso vogliamo costruire un isomorfismo di campi 
$$
f: \mathbb{F}_{p}[X] /\left< p(x) \right> \to \mathbb{F}_{p}[X] / \left< q(x) \right> 
$$
dove $p(x), q(x)\in \mathbb{F}_{p}[X]$ sono monici irriducibili di grado $n$. Basta costruire un morfismo di anelli. Infatti, un morfismo di anelli che sono campi è iniettivo, ed inoltre
$$
|\mathbb{F}_{p}[X] /\left< p(x) \right>| \simeq|\mathbb{F}_{p}[X] / \left< q(x) \right>| = p^{n}
$$
Sia ha che, se $y\in \mathbb{F}_{p}[X] /\left< p(x) \right>$, allora $p(x)\in \mathbb{F}_{p}[X]$ è il polinomio minimo di $y$ su $\mathbb{F}_{p}$. Quindi se $p(x)$ ha una radice in $\mathbb{F}_{p}[X] /\left< p(x) \right>$ possiamo usare la proposizione sull'estensione di morfismi di campi per definire il morfismo $f$ che sarà un isomorfismo. Infatti
$$
\mathbb{F}_{p} \subseteq \mathbb{F}_{p}[X] /\left< p(x) \right>, \mathbb{F}_{p}[X] /\left< q(x) \right> \quad \text{e } \quad \mathbb{F}_{p}[X] /\left< p(x) \right> = \mathbb{F}_{p}([x])
$$
dove $[x]$ è la classe di equivalenza di $x\in \mathbb{F}_{p}[X] /\left< p(x) \right>$. Poiché $\mathbb{F}_{p}[X] /\left< q(x) \right>$ è un campo di spezzamento di $x^{p^{n}}- x$ e $p(x)$ lo divide, allora $p(x)$ fattorizza a fattori di grado $1$ sul campo $\mathbb{F}_{p}[X] /\left< q(x) \right>$.

Tutto questo implica che, dato $\beta \in \mathbb{F}_{p}[X] /\left< q(x) \right>$ tale che $p(\beta)=0$ allora l'assegnazione
$$
c_{0} + c_{1}x + \dots + c_{n-1}x^{n-1} \to c_{0} + c_{1}\beta + \dots + c_{n-1}\beta^{n-1}
$$
definisce un morfismo di anelli
$$
f: \mathbb{F}_{p}[X] /\left< p(x) \right> \to \mathbb{F}_{p}[X] / \left< q(x) \right> 
$$
>[!example]
>In $\mathbb{F}_{3}[X]$ si considerino i polinomi irriducibili $1 + x^{2}$ e $2+x+x^{2}$, entrambi minimi su $x$ e $y$ rispettivamente. Quindi si ha che
>$$
>1+x^{2} = y + y^{2} + x^{2} = x^{2} + 2y^{2} + 2y + 2 = \dots = (x + y + 2)(x + 2y + 1)
>$$
>quindi in $K'[X]$, $1 + x^{2}$ ha le rue radici $-y-2 = 2y + 1$ e $-2y -1 = y + 2$.
>Abbiamo quindi $2$ isomorfismi $f:K \to K'$ e $g: K \to K'$ con rispettivamente $a_{0} + a_{1}x \to a_{0} + a_{1}(2y + 1)$ e $a_{0} + a_{1}x \to a_{0} + a_{1}(y + 2)$

[Lemma]
Se $K$ è un anello commutativo di caratteristica prima $p$, allora
$$
(x + y) ^{p^{h}} = x^{p^{h}} + y^{p^{h}}
$$
per ogni $x,y\in K$ e $h \geq 1$. Da questo lemma segue che, se $K$ è un campo di caratteristica $p$, la funzione
$$
\Phi: K \to K \qquad x \to x^{p}
$$
è un morfismo di campi. Se $K = \mathbb{F}_{p^{n}}$, $\Phi$ si dice **automorfismo**, essendo un morfismo iniettivo da un campo di cardinalità finita in se stesso. Questo è anche chiamato **automorfismo di Frobenius**

[Teorema]
Il gruppo degli automorfismi di $\mathbb{F}_{p^{n}}$ o $Aut(\mathbb{F}_{p^{n}})$ è ciclico di cardinalità $n$, generato dall'automorfismo di Frobenius.

[Lemma]
Sia $F$ un campo. Il polinomio $x^{d} -1 | x^{n}-1$ in $\mathbb{F}[X]$ sse $d|n$. Questo implica $d|n \iff x^{p^{d}}-x|x^{p^{n}}-x$  

[Proposizione]
Tutti e soli i sottocampi di $\mathbb{F}_{p^{n}}$ sono i campi $\mathbb{F}_{p^{d}}$ dove $d |n$

Finora, dato un numero primo $p$ e un numero naturale $n\neq 0$, abbiamo costruito un campo di cardinalità $p^{n}$ prendendo un polinomio irriducibile $q\in \mathbb{F}_{p}[X]$ e facendo il quoziente
$$
\mathbb{F}_{p}[X] /\left< Q \right>
$$
Abbiamo anche visto che due campi costruiti in questo mode, aventi stessa cardinalità, sono isomorfi. Da qui possiamo fare qualche osservazione
1) Sia $K$ un campo finito, qual'è la caratteristica di $K$? 
	Un campo finito ha caratteristica $p$ ed il suo sottocampo fondamentale è $\mathbb{F}_{p}$
2) Sia $K$ un campo finito e $\mathbb{F}_{p} \subseteq K$ per qualche primo. Inoltre il gruppo moltiplicativo $K\setminus \{ 0 \}$ è ciclico e quindi, se $K\setminus \{ 0 \} = \left< \alpha \right> \implies K = \mathbb{F}_{p}(\alpha)$. Quindi se il grado di $\alpha$ su $\mathbb{F}_{p}$ è $n$, abbiamo che $|K|=p^{n}$, ossia **ogni campo finito ha cardinalità** $p^{n}$, per qualche primo e $n\neq 0$ naturale.
3) Siano $K_{1},K_{2}$ di cardinalità $p^{n}$. Sia $K_{1}=\mathbb{F}_{p}(\alpha)$ dove $\alpha$ è generatore del gruppo $K_{1}\setminus \{ 0 \}$ di grado $n$. Sia adesso $q\in \mathbb{F}_{p}[X]$ il suo polinomio minimo. Quindi $deg(q)=n$ e $q$ è irriducibile. 
	1) $K_{1}, K_{2}$ sono campi di spezzamento di $x^{p^{n}} -x\in \mathbb{F}_{p}[X]$
	2) ogni polinomio irriducibile di grado $n$ in $\mathbb{F}_{p}[X]$ è fattore di $x^{p^{n}}-x$
	3) Ne segue che il polinomio $q$ ha una radice in $K_{2}$, sia $\beta$ tale radice
	4) Allora l'assegnazione $\alpha\to\beta$ definisce un morfismo di campi da $K_{1}$ in $K_{2}$ poiché un morfismo di campi è sempre iniettivo, e poiché tale morfismo è suriettivo ed, infine, avendo $|K_{1}|=|K_{2}|$ si ha
$$
K_{1} \simeq K_{2}
$$

[Teorema - Algoritmo di Berlekamp]
Sia $f(x)\in \mathbb{F}_{p}[X]$ di grado $d > 1$, sia $h(x) \in \mathbb{F}_{p}[X]$ di grado $1 \leq deg(h) < d$ tale che $f(x) | h(x)^{p} - h(x)$ allora
$$
f(x) = MCD\{ f(x), h(x) \}\cdot MCD\{ f(x), h(x) - 1 \}\cdot .. \cdot MCD\{ f(x), h(x) - (p - 1) \}
$$
è una fattorizzazione non banale di $f(x) \in \mathbb{F}_{p}[X]$

>[!Dimostrazione]-
>Supponiamo che $f(x)$ divida $h(x)^{p}-h(x)$. Il polinomio $x^{p}-x$ si fattorizza come 
>$$
>x^{p}- x = x(x-1)(x-2)\dots(x-(p-1))
>$$
>banalmente posso sostituire $x$ con $h(x)$ e abbiamo che $MCD\{ h(x) - i, h(x)  -j\} = 1$. Infatti, se $MCD\{ \dots \} = D(x)$ allora
>$$
>\begin{align}
>h(x) - i = D(x)H_{i}(x) \\
>h(x) - j = D(x)H_{j}(x)
>\end{align} \implies
>$$
>$D(x)[H_{i}(x) - H_{j}(x)] = j -i\in \mathbb{F}_{p}\implies Deg(D) = 0$ per $i \neq j$
>Inoltre, se $MCD\{ a,b \} = 1$ si ha che $MCD\{ f, ab \}= MCD\{ f,a \}MCD\{ f,b \}$ si ha che
>$$
>MCD\{ f,a_{1}\dots a_{k} \} = MCD\{ f,a_{1} \}\dots MCD\{ f, a_{k} \}
>$$
>Poiché $f(x) | h(x)^{p}-h(x)$ abbiamo che
>$$
>f(x) = MCD\{ f(x), h(x)^{p}-h(x) \}
>$$
>e visto che, per $i\neq j$, si ha $MCD\{ h(x) - i, h(x) -j \} = 1$ abbiamo che
>$$
>f(x) =  MCD\{ f(x), h(x)^{p}-h(x) \} = MCD\{ f,h \}\dots MCD\{ f, h -p + 1 \}
>$$
>Poiché $Deg(h-1)<deg(f)$ e $MCD\{ f, h - i \} \neq f(x)$. Quindi nella fattorizzazione precedente appaiono solo polinomi di grado $<d$, quindi è una fattorizzazione non banale di $f$.

Possiamo anche mostrare che un polinomio $h(x)\in \mathbb{F}_{p}[X]$ che soddisfa ^^ esiste sempre. 

>[!Dimostrazione]-
> Sia
>$$
>h(x) = b_{0} + b_{1}x + \dots + b_{d-1}x^{d -1}
>$$
>allora 
>$$
>h(x)^{p} = b_{0}^{p} + b_{1}^{p}x^{p} + \dots + b_{d-1}^{p}x^{p(d -1)}
>$$
>>[!note]- Passaggio
>>A quanto pare abbiamo dimostrato da qualche parte che $(x + y)^{p}= x^{p} + y^{p}$.
>
>Ma visto che, $b_{i}^{p}=b_{i}$ possiamo semplificare a 
>$$
>h(x)^{p} = b_{0}^{} + b_{1}^{}x^{p} + \dots + b_{d-1}^{}x^{p(d -1)}
>$$
>e adesso si ha che (roba che non voglio scrivere tanto non mi metto a spiegare sto teorema)

Sia $f(x) = p_{1}(x)\dots p_{k}(x)$ una fattorizzazione di $f(x)\in \mathbb{F}_{p}[X]$ in fattori irriducibili. Supponiamo che $f$ non abbia fattori multipli. [Teorema]
Sia $K$ un campo, allora
1) Se $f(x)\in K[X]$ ha un fattore multiplo, allora $MCD\{ f,f' \} \neq 1$ dove $f'$ è la derivata.
2) Se $K$ ha caratteristica $0$ o è un campo finito di caratteristica $p$ e $MCD\{ f,f' \}\neq 1$, allora $f(x)$ ha sempre un fattore multiplo

Possiamo anche estendere il **teorema cinese dei resti** per i polinomi. Siano $p_{i}(x)$ con $MCD\{ p_{i}(x), p_{j}(x) = 1 \}$
$$
\mathbb{F}_{p}[X] / \left< f \right>  \simeq \mathbb{F}_{p}[X] / \left< p_{1}(x) \right>\times \dots \times \mathbb{F}_{p}[X] / \left< p_{k}(x) \right>
$$
dato $(s_{1}, \dots, s_{k})\in \mathbb{F}_{p}^{k}$, esiste un unica classe $[h(x)] \in \mathbb{F}_{p}[X] /\left< f \right>$ tale che
$$
\begin{cases}
[h(x)] = [s_{1}]  & \text{in } \mathbb{F}_{p}[X] /\left< p_{1}(x) \right>  \\
\quad \vdots \\
 [h(x)] = [s_{k}]  & \text{in } \mathbb{F}_{p}[X] /\left< p_{k}(x) \right>  
\end{cases}
$$
ossia $h(x) - s_{i}$ è divisibile per $p_{i}(x)$, quindi divide
$$
h(x) [h(x) - 1] \dots [h(x) - (p - 1)] = h(x)^{p} - h(x)
$$

>[!example]
>Fattorizziamo $f:x^{5} + x^{2} + 2x + 1 \in \mathbb{F}_{3}[X]$. Prima bisogna verificare che $MCD\{ f,f' \} = 1$
>$$
>MCD\{ f,f' \} = MCD\{  x^{5} + x^{2} + 2x + 1 , 5x^{4} + 2x^{} + 2 \} = 1 \checkmark 
>$$
>Poi bisogna calcolare i resti
>$$
>\begin{align}
>x ^{ 3 (5 -1)} = x^{12}  & \equiv [x^{2} +2]_{f} \\
>x^{3(3)} = x^{9}  & \equiv [2x^{4} + x^{3} + x^{2}+ 2x + 2]_{f} \\
>x^{3(2)} = x^{6}  & \equiv [2x^{3} + x^{2} + 2x]_{f} \\
>x^{3}  & \equiv [x^{3}]_{f} \\
>1  & \equiv [1]_{f} \\
>\end{align}
>$$
>E quindi ho
>$b_{0} + b_{1}x^{3} + b_{2}\underbrace{ (2x^{3} + x^{2 } + 2x ) }_{ x^{6} } + b_{3}\underbrace{ (2x^{4} + x^{3} + x^{2} + 2x + 2) }_{ x^{9} } + b_{4}\underbrace{ (x^{2} + 2 ) }_{ x^{12} } =$$b_{0}+b_{1}x + b_{2} x^{2} + b_{3}x^{3} + b_{4}x^{4}$
>Poi si mette tutto in un sistema e ottengo $(b_{0},b_{1},b_{2},b_{3},b_{4}) = (0,1,1,1,2)$. Quindi $f(x) = MCD\{ f, i + x + x^{2} + x^{3} +2x^{4} : i=0,1,2\} = (1 + x^{2}) (x^{3} + 2x+1)$

Sia $f(x)\in \mathbb{F}_{p}[X], deg(f) = d$ e sia $f(x)=p_{1}(x)p_{2}(x)\dots p_{k}(x)$ una fattorizzazione in fattori irriducibili non banali aventi tutti molteplicità $1$. Siano
$$
\begin{align}
r_{0} &  = [1]_{f} \\
r_{1} & =[x^{p}]_{f} \\
 & \vdots   \\
r_{d-1} &  = [x^{d-1}p]_{f}
\end{align}
$$
con $deg(r_{i}) <d$. Definiamo la matrice $A \in Mat_{d\times d}(\mathbb{F}_{p})$ come la matrice dei coefficienti del termine di grado $i$ del polinomio $r_j(x)$ -- ovvero prendo la matrice del sistema -- e possiamo risolvere con il classico $(A - I)\bar{b} = \bar{0}$.

[Teorema]
Il numero di fattori irriducibili $k$ nella fattorizzazione di $f$ è uguale alla dimensione del nucleo di $A - I$, ossia
$$
k = d - Rango(A - I)
$$
Se $f\in \mathbb{F}_{p}[X]$ ha fattori irriducibili di molteplicità $>1$, procediamo nel seguente modo.
$$
D = MCD \{ f,f' \}\neq 1
$$
osserviamo che $f /D$ ha fattori irriducibili tutti di molteplicità $1$. Infatti se $p_{1}, \dots, p_{k}$ sono tutti distinti abbiamo che
$$
f / D = p_{1}\dots p_{k}
$$
Adesso fattorizziamo sia $f /D$ che $D$ e andiamo avanti ripetendo finché non si arriva a
$$
MCD\{ D_{i}, D_{i}' \} = 1
$$

>[!example]
>In $\mathbb{F}_{3}[X]$ consideriamo $f(x) = 1 + 2x + 2x^{2} + x^{5} + x^{6} + x^{7}$. Si ha che $f' = 2 + x + 2x^{4} + x^{6}$ e $MCD\{ f,f' \} = 1 + 2x + x^{3} = D$. Quindi $f /D = 1 + 2x^{2} + x^{3} + x^{4}$ che fattorizzandolo si trova $f /D = (x +1)(1 + 2x + x^{3})$. Poiché $D$ non ha radici in $\mathbb{F}_{3}$, è irriducibile. Allora 
>$$
>f = f /D \cdot D = (x+1)(1 + 2x + x^{3})^{2}
>$$


