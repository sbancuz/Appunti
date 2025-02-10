---
tags:
  - logica_algebra
---
La logica modale è un'estensione della [[Propositional logic]]. L'alfabeto è lo stesso a cui si aggiungono i connettivi modali; l'alfabeto quindi diventa
1) Un insieme numerabile di variabili
2) I connettivi logici
3) Simboli ausiliari $()$
4) I connettivi modali $\square,\diamond$ che significano rispettivamente *è necessario che* e *è possibile che* 

Le parole del linguaggio sono le formule ben formate definite in modo ricorsivo:
1) Ogni variabile è un FBF
2) Se $A$ è un FBF, allora $(\lnot A), (\square A), (\diamond A)$ sono FBF
3) Se $A,B$ sono FBF, allora $(A \land B), (A \lor B), (A \implies B), (A \iff B)$ sono FBF

Secondo questa lettura i connettivi modali possono essere definiti uno in termini dell'altro
$$
\begin{align}
\square A  & \equiv \lnot \diamond \lnot A \qquad  &   \text{è necessario }\equiv \text{non è possibile non }A \\
\diamond A  & \equiv \lnot \square \lnot A  \qquad  & \text{è possibile }\equiv\text{non è necessario non }A
\end{align}
$$
La logica proposizionale è una logica vero-funzionale: assegnando valori $0$ o $1$ alle variabili possiamo assegnare un valore $0$ o $1$ ad una formula nel modo univoco stabilito nella sezione [[Propositional logic#Semantics]], che corrisponde alla nostra intuizione di negazione, disgiunzione, congiunzione. Per la logica modale dobbiamo anche interpretare l'operatore della **necessità** e della **possibilità**.

>[!example]
>Sia $\square A \implies \diamond A, A\implies \diamond A$, è vera $A \implies \square\diamond A$? Non è chiaro se sia vera o false. 

Ci sono vari tipi di logica semantica
1) Epistemica $\to$ $\square A$ diventa *si sa che* $A$
2) Deontica $\to$ $\square A$ diventa *è obbligatorio che* $A$
3) Doxatica $\to$ $\square A$ diventa *si crede che* $A$ 
4) Dimostrativa $\to$ $\square A$ diventa *è dimostrabile che* $A$
### Semantica di Kripke

Un **frame** è una coppia $(S,R)$, dove $S$ è un insieme non vuoto, detto **insieme dei mondi**, e $R \subseteq S\times S$ è una [[Relazione]] su $S$, detta **relazione di accessibilità**. Un frame può essere rappresentato con un grafo diretto con cappi i cui vertici sono gli elementi dell'insieme $S$ e ho una freccia dal vertice $x$ a $y$ se $(x,y)\in R$

>[!example]
>Il frame $(S,R)$ dove $S = \{ 2,3,4,5,6 \}$ e $R = \{ (x,y)\in S\times S : x \text{ divide } y \}$ è
>```tikz
>\begin{document}
>
>\begin{tikzpicture}[scale=1, every node/.style={draw, circle, inner sep=2pt}]
% Nodes
\node (2) at (0, 0) {2};
\node (3) at (2, -1) {3};
\node (4) at (4, -1) {4};
\node (5) at (6, -1) {5};
\node (6) at (8, -1) {6};
% Loops
\draw[->] (2) edge[out=150, in=120, looseness=10] (2);
\draw[->] (3) edge[out=150, in=120, looseness=10] (3);
\draw[->] (4) edge[out=150, in=120, looseness=10] (4);
\draw[->] (5) edge[out=150, in=120, looseness=10] (5);
\draw[->] (6) edge[out=150, in=120, looseness=10] (6);
% Arrows between nodes
\draw[->] (2) to[bend left] (3);
\draw[->] (2) to[bend left=25] (4);
\draw[->] (2) to[bend left=35] (6);
% Cross on node 6
\draw[thick] (7.7, -1.3) -- (8.3, -0.7);
\draw[thick] (7.7, -0.7) -- (8.3, -1.3);
\end{tikzpicture}
\end{document}
>```

Un **modello** di un frame $(S,R)$ è una terna $(S,R,V)$ dove
$$
V: Var \to  \underbrace{\mathcal  P(S) }_{ \text{insieme delle parti} }
$$
è detta **funzione di valutazione**. Una formula $F$ si dice **vera in un mondo $x$ del modello $M$** e scriviamo $M  \vDash_{x} F$ sse:
1) $F$ è una variabile, quindi $x\in V(F)$
2) $F$ è $\lnot y$ e $y$ è una variabile, quindi $x\notin V(Y)$
3) $F$ è del tipo $\lnot G$, dove $G$ è una formula, quindi $M \cancel{ \vDash_{x} } G$
4) $F$ è del tipo $G_{1}\land G_{2}$ o $G_{1} \lor G_{2}$
5) $F$ è del tipo $\square G$, quindi per ogni $y\in S$ tale che $(x,y)\in R$
6) $F$ è del tipo $\diamond G$, quindi esiste un mondo $y\in S$ tale che $(x,y)\in R$

Una formula è **soddisfacibile** se esiste un modello $M=(S,R,V)$ e un mondo $x\in S$ tale che $M \vDash_{x}F$

[Teorema]
Se una formula modale $F$ è soddisfacibile, allora è soddisfacibile in una struttura di Kripke $(S,R)$ tale che 
$$
|S| \leq 2 ^{|F|}
$$
quindi il problema di soddisfacibilità di una formula modale è decidibile

La verità di una formula del linguaggio della logica modale dipenderà quindi dal frame scelto, in particolare, dalla relazione $R$.  

>[!example]
>Nella logica della necessità $\square x \implies x$ si legge *è necessario che $x$, allora $x$*, ma nella Deontica diventa *è obbligatorio che $x$, allora $x$* e non vogliamo che questa sia sempre vera. 
>Perché sia vera la formula, la relazione $R$ del frame deve essere riflessiva.
>

Sia $Z = V(X), Z\subseteq S$, tale che $y \in Z$ -- quindi $x$ è falsa nel mondo $y$. Sia $\{ z \in S : (y,z) \in R \} \subseteq Z$ -- $x$ sia vera in tutti i mondi accessibili da $y$. Allora, se $M=(S,R,V)$
$$
M \vDash _{y} \square X \qquad \text{ ma } \qquad M \cancel{ \vDash _{y} } X
$$

>[!note]
>Nella logica Deontica, dove non vogliamo che questo risultato sia vero, non prenderemo la relazione riflessiva
 
Una formula **vera in un modello** $M$ si indica con $M \vDash F$, se $M \vDash_{x} F, \forall {x\in S}  {}$. Una formula si dice **valida in un frame** $(S,R)$ se è vera in tutti i modelli costruiti su $(S,R)$ e si scrive $(S,R) \vDash F$

>[!example]
> $\square x \implies x$ è vera nei frame $(S,R)$ in cui $R$ è riflessiva

Una formula è valida (in generale) sse è valida su ogni frame e la indichiamo con $\vDash F$.

Uno **schema di formule** è una collezione di formule aventi tutte una stessa forma sintattica. Le tautologie della logica proposizionale sono valide su ogni frame.

Vediamo ora che lo schema di formule qui sotto è valido su ogni frame.
$$
\square(A \implies B) \implies (\square A \implies \square B)
$$
>[!Dimostrazione]-
>Sia $w\in S$ un mondo e $M$ un modello su un frame $(S,R)$. Sia $M \vDash_{w} \square(A \implies B)$ e $M \vDash_{w} \square A$. La prima significa che $M \vDash_{v} A\implies B$ per ogni $v \in S$ tale che $(w,v)\in R$. La seconda significa $M \vDash_{v} A$ per ogni $v\in S$ tale che $(w,v)\in R$. 
>Dunque $M \vDash_{v} B$ per ogni $v\in S$ tale che $(w,v)\in R$, ossia $M \vDash _w\square B$. Quindi abbiamo mostrato che questo schema è valido.

Possiamo anche mostrare che i seguenti schemi sono validi:
1) $\square(A \land B) \iff (\square A \land \square B)$
2) $\diamond(A \lor B) \iff (\diamond A \lor \diamond B)$
3) $\square(A \implies B) \implies (\diamond A \implies \diamond B)$
4) $\diamond(A \implies B) \implies (\square A \implies \diamond B)$

Invece i seguenti schemi non lo sono:
1) $\diamond A \implies \square A$
2) $\square A \implies A$
3) $\square A \implies \square \square A$
4) $\square(A \implies B)\implies (\square A \implies \diamond B)$
5) $\square (\square A \implies B) \lor \square(\square B \implies A)$
6) $\square (A \lor B) \implies (\square A \lor \square B)$
7) $\square (\square A \implies A) \implies \square A$
### Corrispondenza e non esprimibilità

Diciamo che un frame $(S,R)$ gode di una certa proprietà se ne gode la relazione $R$. In molti casi una proprietà di un frame equivale alla validità di uno schema di formule modali nei frame con quella proprietà. 

[Teorema]
Lo schema $\square A \implies A$  è valido in un frame $(S,R)$ sse $R$ è riflessiva.

>[!Dimostrazione]-
>Sia $R$ non riflessiva, allora c'è un mondo $y\in S$ tale che $(y,y)\notin R$. Sia $Z = V(X), Z\subseteq S$, tale che $y \notin Z$ -- quindi $x$ è falsa nel mondo $y$. Sia $\{ z \in S : (y,z) \in R \} \subseteq Z$ -- $x$ sia vera in tutti i mondi accessibili da $y$. Allora, se $M=(S,R,V)$
>$$
>M \vDash _{y} \square X \qquad \text{ ma } \qquad M \cancel{ \vDash _{y} } X
>$$

[Teorema]
Lo schema $A \implies \square\diamond A$ è valida in un frame $(S,R)$ sse $R$ è simmetrica.

>[!Dimostrazione]-
>Sia $R$ simmetrica, ossia $(x,y)\in R \implies (y,x)\in R$. 
>Sia $M \vDash_{w}A$ e $(w,v)\in R$. Dunque $(v,w)\in R$. Per ogni $v \in S$ ho $(w,v)\in R$ tale che $M \vDash_{v} \diamond A$, ossia $M \vDash_{w}\square\diamond A$.
>Adesso assumiamo che lo schema sia valido in $(S,R)$, sia $x$ una variabile $V(x)= \{ s \}$, sia $t\in S$ tale che $(s,t)\in R$. Quindi $M \vDash_{S}x$. Dalla validità dello schema segue allora che
>$$
>M \vDash _{S}\square\diamond X
>$$
>da cui $M \vDash_{t}\diamond X$. Quindi esiste $r\in S$ tale che $(t,r)\in R$ e $M \vDash _rX$, ossia $r=s$

[Teorema]
Lo schema $\square A\implies\square\square A$ è valido in un frame $(S,R)$ sse $R$ è transitiva

>[!Dimostrazione]-
>Sia $R$ transitiva e sia $M \vDash_{w} \square A$, ossia $M \vDash_{v} A$ per ogni $v\in S$ tale che $(w,v)\in R$. Sia $u\in S$ tale che $(v,u)\in R$, con $(w,v)\in R$ allora $(w,u)\in R$ e quindi $M \vDash_{v}\square A$ per ogni $v\in S$ tale che $(w,v)\in R$, ossia $M \vDash_{w}\square\square A$. Assumiamo adesso che sia valido lo schema $(S,R)$. Sia $x$ una variabile $s\in S$ e $V(x) = \{ w \in S : (s,w)\in R \}$. 
>Allora $M \vDash_{S}\square x$ e quindi, per la validità dello schema, $M \vDash_{S}\square\square x$, da cui $M \vDash_{t}\square x$ per ogni $t\in S$ tale che $(s,t)\in R$, ossia $M \vDash_{r}X$ per ogni $r\in S$ tale che $(t,r)\in R$, $(s,t)\in R$. Da ciò segue che $r\in V(x)$ ossia $(s,t)\in R$ e $(t,r)\in R$ => $(s,r)\in R$ 

Siano $(S_{1}, R_{1})$ e $(S_{2},R_{2})$ due frame. Una funzione 
$$
f: S_{1} \to S_{2}
$$
è un **morfismo di frame** se $(x,y)\in R_{1} \implies (f(x),f(y))\in R_{2}$

Siano $M_{1} = (S_{1},R_{1},V_{1})$ e $M_{2}=(S_{2},R_{2},V_{2})$ due modelli. Un morfismo di frame $f:(S_{1},R_{1})\to(S_{2},R_{2})$ è un **morfismo di modelli** se:
8) $w\in V_{1}(x) \iff f(w) \in V_{2}(x), \forall {w} \in  {S_{1}}, x\in Var$
9) $(f(w),y)\in R_{2} \implies \exists {v}\in  {}S_{1}$ tale che $(w,v)\in R_{1}$ e $f(v)=y$ $\forall {w} \in {S_{1}},y\in S_{2}$

>[!note]
>I morfismi di modelli sono solitamente detti **p-morfismi**.

[Lemma 1]
Sia $f:(S_{1},R_{1},V_{1})\to(S_{2},R_{2},V_{2})$ un morfismo dal modello $M_{1}$ al modello $M_{2}$ allora
$$
M_{1} \vDash _{w} F \text{ sse } M_{2} \vDash _{f(w)}F
$$
>[!Dimostrazione]-
>Se $F$ è una variabile, allora $M_{1} \vDash_{w}F$ sse $w\in V_{1}(F)$ e questo è vero sse $f(w)\in V_{2}(F)$ sse $M_{2} \vDash_{f(w)}F$.
>Per gli altri tipi di formule, si dimostra induttivamente sulla costruzione della formula. Per il caso in cui $F =\diamond G$. Sia $M_{1} \vDash_{w}\diamond G$. Allora esiste $v\in S_{1}$ tale che $(w,v)\in R_{1}$ e $M_{1} \vDash_{v}G$.
>Poiché $(f(w), f(v))\in R_{2}$ in quanto $f$ è un morfismo di modelli, e induttivamente $M_{2} \vDash_{f(v)}G$ allora $M_{2} \vDash_{f(w)}\diamond G$.
>Sia $M_{2}\vDash_{f(w)}\diamond G$. Allora esiste $u\in R_{2}$ tale che $(f(w), u)\in R_{2}$ e $M_{2} \vDash_{u} G$.
>Per la condizione $2$ nella definizione di morfismo di modelli, esiste $v\in S_{1}$ tale che $(w,v)\in R_{1}$ e $f(v)=u$. 
>Per l'ipotesi induttiva, $M_{1} \vDash_{v}G$ e quindi $M_{1} \vDash_{w} \diamond G$

[Lemma 2]
Sia $f:(S_{1},R_{1},V_{1})\to(S_{2},R_{2},V_{2})$ un morfismo dal modello $M_{1}$ al modello $M_{2}$. Se $f$ è suriettivo, allora 
$$
M_{1} \vDash F \text{ sse } M_{2} \vDash F
$$
per ogni formula.

>[!Dimostrazione]-
>$M_{1} \vDash F$ sse $M_{1}\vDash_{w} F$ per ogni $w\in S_{1}$ sse $M_{2}\vDash_{f(w)}F$ per ogni $w\in S_{1}$ sse $M_{2} \vDash F$, perché $f$ è suriettivo

[Lemma 3]
Sia $f:(S_{1},R_{1})\to(S_{2},R_{2})$ un morfismo di frame tale che valga la condizione $2$ del morfismo di modelli. Allora esiste un modello $M_{1}$ su $(S_{1},R_{1})$ tale che $f: M_{1}\to M_{2}$ è un morfismo di modelli.

>[!Dimostrazione]-
>Basta definire $M_{1}=(S_{1},R_{1},V_{1})$ con $V_{1}(x) = \{ w\in S_{1} : M_{2} \vDash_{f(w)}X  \}$

[Lemma 4]
Sia $f:(S_{1},R_{1})\to(S_{2},R_{2})$ un morfismo di frame tale che valga la condizione $2$ del morfismo di modelli. Se $f$ è suriettivo si ha che 
$$
(S_{1}, R_{1}) \vDash  F \implies (S_{2},R_{2}) \vDash F
$$
per ogni formula $F$.

>[!Dimostrazione]-
>Sia $(S_{2},R_{2}) \cancel{ \vDash }F$. Allora esiste un modello $M_{2}$ su $(S_{2},R_{2})$ tale che $M_{2} \cancel{ \vDash } F$. Per il lemma 3, esiste un modello $M_{1}$ su $(S_{1},R_{1})$ tale che $f:M_{1} \to M_{2}$ è un morfismo di modelli. Poiché $f$ è suriettivo, per il lemma $2$ si ha che $M_{1} \cancel{ \vDash } F$. Quindi $(S_{1},R_{1}) \cancel{ \vDash }F$

[Teorema]
L'antisimmetria non è esprimibile, ossia non esiste una formula $F$ tale che $(S,R)\vDash F$ sse $R$ è antisimmetrica.

>[!Dimostrazione]-
>A pagina $9$ del terzo se ho voglia
### Logiche modali normali

Lo schema di formule $def_{\diamond} : \diamond \iff \lnot\square \lnot A$ è valido, $\vDash def_{\diamond}$

Sia $X$ una variabile e $F$ una formula. Definiamo la **sostituzione uniforme** di $F$ al posto di $X$ un una formula $G$. Quindi scriviamo
$$
G[F / X]
$$
La formula ottenuta da $G$ dove ogni occorrenza di $X$ è stata sostituita con $F$. Una **logica modale normale** è un insieme di formule tale che
10) $\Gamma$ contiene tutte le tautologie della logica proposizionale
11) $\Gamma$ contiene tutte le istanze dello schema $K: \square(A \implies B)\implies(\square A \implies \square B)$
12) $\Gamma$ contiene tutte le istanze dello schema $def_{\diamond}: \diamond A \iff \lnot\square \lnot A$
13) è chiuso sotto **modus ponens**, quindi se $A\in \Gamma$ e $(A\implies B)\in \Gamma$ allora $B\in \Gamma$
14) è chiuso sotto **necessitazione**, quindi se $A\in \Gamma$ allora $\square A\in \Gamma$
15) è chiuso sotto **sostituzione uniforme**, quindi se $A\in \Gamma$ allora $A[B / X]\in \Gamma$

La **logica modale** $K$ è definita dai seguenti schemi di assiomi e regole:
16) Assiomi $\to$ $1,2,3$ sopra
17) Regole di inferenza $\to$ $4,5,6$ sopra

Data una logica modale $L$, una **dimostrazione** in $L$ è una successione finita di formule tali che o
- ognuna è un assioma
- è ottenuta dalle formule precedenti dalla successione via applicazione di inferenza

Una formula $F$ si dice **teorema** di $L$, e scriviamo 
$$
\vdash _{L}F
$$
sse esiste una dimostrazione in $L$ la cui ultima formula è $F$. 

[Teorema]
L'insieme $\{ F: \vdash_{K}  F\}$ è chiuso sotto sostituzione uniforme.

Nelle logiche epistemiche si estende la logica $K$ aggiungendo lo schema di assiomi
$$
\square F \implies F
$$
La logica $K$ a cui aggiungiamo questo assioma è detta **logica T**. I teoremi della logica normale $T$ sono validi su frame riflessivi. Se accettiamo il **principio di introspezione epistemica positiva**,  ossia se assumiamo che ogni volta che si sa qualcosa si sa di sapere, aggiungiamo l'assioma
$$
\square F \implies \square \square F
$$
Abbiamo cosi definito la **logica $S 4$**. I suoi teoremi sono validi su frame riflessivi e transitivi. Se accettiamo anche il **principio di introspezione negativa**, ossia che ogni volta che non sappiamo qualcosa, sappiamo di non saperla aggiungiamo 
$$
\lnot \square F \implies\square \lnot \square F
$$
E questa è la logica $S 5$. I suoi teoremi sono validi su frame riflessivi, simmetrici e transitivi -- ossia sono validi sulle relazioni di equivalenza.

Una logica è **valida** se $\vdash_{L}A \implies \vDash A$. [Teorema] La logica $K$ è valida.
Una logica è **completa** se $\vDash A \implies \vdash_{L} A$. [Teorema] La logica $K$ è completa.