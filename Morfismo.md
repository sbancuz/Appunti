---
tags:
  - logica_algebra
---
Siano $M_{1}, M_{2}$ monoidi con [[Identità]] $e_{1},e_{2}$. Una funzione $f:M_{1} \to M_{2}$ è un **morfismo di monoidi** se
1) $f(e_{1}) = e_{2}$
2) $f(xy) = f(x)f(y)$

Il **nucleo** di un morfismo di monoidi $f:M_{1} \to M_{2}$ è il [[Monoide#Sottomonoide]] di $M_1$ definito così
$$
Ker(f) = \{ x \in M_{1} : f(x) = e_{2} \}
$$
>[!note]
>Da definizione il kernel di un monoide ha sempre al suo interno l'identità

Il nucleo di un morfismo di [[Gruppo|Gruppi]] è definito come per [[Monoide|Monoidi]]. In aggiunta il $Ker(f)$ è un [[Gruppo#Sottogruppo]] di $G_{1}$ e $Im(f)$ è un [[Gruppo#Sottogruppo]] di $G_{2}$
### Isomorfismo

Un isomorfismo di monoidi (o di gruppi) è un morfismo biunivoco tale che la funzione inversa sia un morfismo. Sia $f: M_{1} \to M_{2}$ un morfismo di monoidi. Se $f$ è biunivoco allora è un isomorfismo

>[!note]- Dimostrazione
>Basta far vedere che la funzione inversa $f^{-1}: M_{2} \to M_{1}$ è un morfismo di monoidi. 
>1) Poiché $f(e_{1}) = e_{2}$ abbiamo che $f^{-1}(e_{2}) = e_{1}$
>2) $f^{-1}(x_{2}y_{2})=f^{-1}(f(x_{1})f(x_{2}))=f^{-1}(f(x_{1}x_{2})) =x_{1}x_{2}=f^{-1}(x_{2})f^{-1}(y_{2})$

Ovviamente si estende anche ad i gruppi e viene indicato con $\simeq$.

Si può anche vedere come ogni monoide finito è isomorfo ad un monoide di [[Matrix|Matrice]] quadrate, dove l'operazione è il prodotto righe per colonne. Sia $M = \{ x_{1},\dots,x_{n} \}$ un monoide con $|M| =n \in \mathbb{N}$ e identità $e=x_{1}$. Per ogni $x\in M$ definiamo una matrice $A(x) \in Mat_{n\times n}(\mathbb{Z})$ nel seguente modo
$$
A(x)_{ij} = \begin{cases}
1  & xx_{j} = x_{i} \\
0  & \text{altrimenti} 
\end{cases}
$$
La funzione $\mathcal F: M \to Mat_{n\times n}(\mathbb{Z}) : x \to A(x)$ è iniettiva. Infatti se $A(x) = A(y)$ allora $A(x)_{i1} = A(y)_{i 1}$. È inoltre facile dimostrare che $\mathcal F$ è un morfismo di monoidi e quindi $\mathcal F: M \to Im(\mathcal F)$ è un isomorfismo di monoidi.

Il prodotto righe per colonne corrisponde alla composizione di funzioni. Quindi un monoide finito di cardinalità $n$ è isomorfo a un sottomonoide del monoide delle funzioni $f$ da $\{ 1,\dots, n \}$ in $\{ 1,\dots,n \}$ con la composizione.

Un elemento $x \in M$ di un monoide finito è invertibile sse la matrice associata è invertibile, quindi sse il suo determinante non è $0$ ed è invertibile, o sse la funzione associata è biunivoca.

>[!Teorema di cayley]
Da questo segue che un gruppo finito $G$ di cardinalità $|G| = n$ è isomorfo ad un gruppo di matrici le cui componenti sono $0,1$ e che hanno un unico $1$ in ogni riga/colonna; anche dette **matrici di permutazione**

Il gruppo è inoltre isomorfo ad un sottogruppo del gruppo delle funzioni biunivoche che abbiamo chiamato il gruppo simmetrico $S_{n}$

---

[Teorema]
Sia $f:G_{1}\to G_{2}$ un morfismo di [[Gruppo|Gruppi]]. Allora $f$ è iniettivo $\iff$ $Ker(f) = \{ e_{1} \}$. 

>[!note]- Dimostrazione
>Sia $f$ iniettivo. Sia $x\in Ker(f)$. Allora $f(x)=e_{2}$ e quindi, poiché anche $f(e_{1})=e_{2}$ si ha che $x=e_{1}$ utilizzando l'ipotesi che $f$ sia iniettiva. Quindi sia il $Ker(f) = \{ e_{1} \}$ e siano $x,y \in G_{1}$ tali che $f(x)=f(y)$, abbiamo che $f(x)f(y^{-1})=e_{2}\implies xy^{-1}=e_{1}\in Ker(f) \implies x=y$

Quando si parla di morfismi di monoidi vale solo $f$ è iniettivo $\implies$ $Ker(f) = \{ e_{1} \}$

[Teorema]
Sia $f:G_{1}\to G_{2}$ un morfismo di gruppi abeliani. Allora esiste un morfismo iniettivo $\phi:G_{1} /Ker(\phi)\to G_{2}$ tale che il seguente diagramma è commutativo
```tikz
\begin{document}
\begin{tikzpicture}[ baseline=(current bounding box.center), node distance=3cm, Increased distance every node/.style={font=\large}, edge/.append style={line width=1pt} ]
% Nodes
\node (G1) {$G_1$};
\node (G2) [right of=G1, xshift=2cm] {$G_2$};
\node (Quot) [below of=G1, yshift=-1cm] {$G_1 / \ker(f)$};
% Arrows 
\draw[->] (G1) to node[above] {\large $f$} (G2);
\draw[->] (G1) to node[left] {\large $\pi$} (Quot);
\draw[->] (Quot) to node[below right] {\large $\varphi$} (G2);
\end{tikzpicture}
\end{document}
```

In particolare $G_{1}/Ker(f)\simeq Im(f)$.

>[!note]- Dimostrazione
>L'assegnazione $[g]\to f(g)$ definisce una funzione $\phi:G_{1}/Ker(\phi) \to G_{2}$, infatti se $g'\sim g$ allora $g=g'+h$ che quindi implica $f(g) = \underbrace{ f(g'+h) = f(g') + \underbrace{ f(h) }_{ \text{identità }  } }_{ \text{Proprietà dei morfismi} } = f(g')$. Poiché $f$ è morfismo di gruppi, anche $\phi$ lo è, inoltre
>$$
>Ker(\phi) = \{ [g] \in G_{1} /Ker(f) : \phi([g]) = 0_{2} \} = \{ [0_{1}] \}
>$$
>Quindi $\phi$ è iniettivo. Infine visto che $\phi: G_{1} / Ker(f) \to Im(f)$ è un morfismo di gruppi suriettivo. Allora è anche un isomorfismo.
#### Morfismo di anelli

Possiamo definire il morfismo di [[Anello|Anelli]] come la funzione $f:A \to B$ con $A,B$ anelli, se
$$
f :(A,+)\to(B, +)
$$
è un morfismo di gruppi e
$$
f:(A, \cdot) \to (B, \cdot)
$$
è un morfismo di monoidi. Il nucleo di un morfismo di anelli è l'insieme
$$
Ker(f) = \{ a \in A : f(a) = 0 \}
$$
ed è un [[Ideale]] di $A$. 

[Teorema]
Sia $f:A\to B$ un morfismo di anelli commutativi. Allora esiste un morfismo iniettivi di anelli $\psi: A /Ker(f) \to B$ tale che il seguente diagramma è commutativo

```tikz
\begin{document}
\begin{tikzpicture}[ baseline=(current bounding box.center), node distance=3cm, Increased distance every node/.style={font=\large}, edge/.append style={line width=1pt} ]
% Nodes
\node (G1) {$G_1$};
\node (G2) [right of=G1, xshift=2cm] {$G_2$};
\node (Quot) [below of=G1, yshift=-1cm] {$G_1 / \ker(f)$};
% Arrows 
\draw[->] (G1) to node[above] {\large $f$} (G2);
\draw[->] (G1) to node[left] {\large $\pi$} (Quot);
\draw[->] (Quot) to node[below right] {\large $\psi$} (G2);
\end{tikzpicture}
\end{document}
```
In particolare, se $f$ è suriettivo
$$
\psi: A /Ker(f) \to B
$$
è un isomorfismo di anelli.

>[!Dimostrazione]-
>Dobbiamo solo far vedere che $\phi([a])=f(a), \forall {[a]\in A/I} {}$ è morfismo di anelli. Il resto segue dalla dimostrazione per gli isomorfismi di gruppi.
>- $\phi([1_{A}]) = f(1_{A}) = 1_{B}$
>- $\phi([a][b])=\phi([ab])=f(ab)=f(a)f(b)=\phi([a])\phi([b])$

[Teorema - Teorema cinese dei resti]
Siano $n_{1},n_{2},\dots,n_{k} \in \mathbb{N}\setminus \{ 0,1 \}$ tali che $MCD\{ n_{i,}n_{j} \} = 1$ per ogni $1 \leq i,j\leq k, i\neq j$. Sia $n = n_{1}n_{2}\dots n_{k}$ allora la funzione $\Psi$ è **isomorfismo di anelli**.
$$
\begin{align}
\Psi   :\quad &  \mathbb{Z}_{n}  \to   \mathbb{Z}_{n_{1}}\times \mathbb{Z}_{n_{2}}\times\dots\times \mathbb{Z}_{n_{k}} \\
 & [x]_{n}  \to   ([x]_{n_{1}},[x]_{n_{2}},\dots,[x]_{n_{k}})
\end{align}
$$
>[!note]- Dimostrazione
>Vediamo prima di tutto che la funzione $f$ è un morfismo di anelli, dove $f:\mathbb{Z}\to\mathbb{Z}_{n_{1}}\times\dots\times \mathbb{Z}_{n_{k}}$ è definita da $f(x) = ([x]_{n_{1}}, \dots, [x]_{n_{k}})$
>- $f(a + b) = ([(a+b)]_{n_{1}}, \dots) = ([a]_{n_{1}},\dots) + ([b]_{n_{1}},\dots) = f(a) + f(b)$
>- $f(1) = ([1]_{n_{1}, \dots})$ è l'unità
>- $f(a  b) = ([(ab)]_{n_{1}}, \dots) = ([a]_{n_{1}},\dots) ([b]_{n_{1}},\dots) = f(a) f(b)$
>Adesso bisogna mostrare che il morfismo sia suriettivo. Sia $([a_{1}]_{n_{1}}, \dots, [a_{k}]_{n_{k}})$ osserviamo che 
>$$
>MCD\{ n_{i}, n_{1}n_{2}\dots n_{k} \} = 1
>$$
>Quindi abbiamo l'identità di Bézout $\underbrace{ c_{i}n_{i} }_{ u_{i} } + \underbrace{ b_{i} \frac{n}{n_{i}} }_{ v_{i} } = 1$. Adesso definiamo $x = a_{1}v_{1} + \dots + a_{k}v_{k}$ e abbiamo che
>$$
>f(x) = ([x]_{n_{1}}, \dots, [x]_{n_{k}})
>$$
>infatti
>$$
>[v_{i}]_{n_{j}} = \begin{cases}
>[0]_{n_{j}}  & i \neq j \\
>[1]_{n_{j}} & \text{altrimenti}
>\end{cases}
>$$
>Per il teorema di isomorfismo abbiamo che $\mathbb{Z} /Ker(f) \simeq \mathbb{Z}_{n_{1}}\times\dots\times \mathbb{Z}_{n_{k}}$ come anelli. Ma abbiamo che $Ker(f) = \left< n_{1} \right>\cap \dots \cap \left< n_{k} \right> = \left< mcm\{ n_{1},\dots,n_{k} \} \right> = \left< n_{1}\dots n_{k} \right>$ e visto che $n_{i}, n_{j}$ sono coprimi, l'isomorfismo $\Psi$ è quello enunciato dal teorema.

[Corollario]
Sia $U(\mathbb{Z}_{n})$ il gruppo degli elementi invertibili dell'anello $\mathbb{Z}_{n}$. Sia $n=n_{1}\dots n_{k}$, dove $MCD\{ n_{i}, n_{j} \} = 1$ $\forall {1\leq i,j} \leq k {,i\neq j}$ e $n_{i}\in \mathbb{N} \setminus \{ 0,1 \}, \forall {1\leq} i {\leq k}$ allora come gruppi
$$
U(\mathbb{Z}_{n})\simeq U(\mathbb{Z}_{n_{1}})\times\dots\times U(\mathbb{Z}_{n_{k}})
$$
Poiché un elemento $[x]\in \mathbb{Z}_{n}$ è invertibile sse esiste un'identità di Bézout $ax + bn =1$, abbiamo che $[x]$ è invertibile sse $MCD\{ x,n \}=1$. Quindi
$$
\left| U(\mathbb{Z}_{n}) \right| = \phi(n) \qquad \text{Funzione di eulero}
$$
[Corollario]
Sia $\phi:\mathbb{N}\setminus \{ 0 \} \to \mathbb{N}\setminus \{ 0 \}$ la funzione $\phi$ di Eulero. Siano $x,y\in \mathbb{N}\setminus \{ 0 \}$ tali che $MCD\{ x,y \}= 1$ allora
$$
\phi(xy) = \phi(x)\phi(y)
$$

Come conseguenza del corollario otteniamo una formula per calcolare la funzione $\phi$ di Eulero. Se $p$ è un numero primo, ci sono $p^{k}$ numeri maggiori o uguali a $1$ e minori o uguali a $p^{k}$. Di questi, i numeri $p,2p,\dots,p^{k-1}$ hanno fattori comuni con $p^{k}$. Quindi 
$$
\phi(p^{k}) = p^{k} - p^{k-1}
$$
Se $n=p^{k_{1}}-p^{k_{s}}$, per il corollario
$$
\phi(n) = \phi(p_{1}^{k_{1}})\dots\phi(p_{s}^{k_{s}}) = p_{1}^{k_{1}}\dots p_{s}^{k_{s}} \prod_{\underbrace{ p | n }_{ p \text{ primo} }}\left( 1- \frac{1}{p} \right) = n  \prod_{\underbrace{ p | n }_{ p \text{ primo} }}\left( 1- \frac{1}{p} \right)
$$
[Teorema - Teorema di Eulero]
Siano $n,a\in \mathbb{N} \setminus \{ 0 \}$ tali che $MCD\{ a,n \} = 1$. Allora
$$
[a^{\phi(n)}] = [1] \quad \text{in }\mathbb{Z}_{n}
$$
>[!note]- Dimostrazione
>Sappiamo che la cardinalità del gruppo degli elementi invertibili di $\mathbb{Z}_{n}$ è $|U(\mathbb{Z}_{n})|=\phi(n)$. Sia $\left< [a] \right> \subseteq U(\mathbb{Z}_{n})$ . Allora $|\left< [a] \right>|$ divide $\phi(n)$, ossia $\phi(n) = k \underbrace{ |\left< [a] \right>| }_{ c }$, per qualche $k \in \mathbb{N}$. Abbiamo quindi che
>$$
>[1] = [a^{c}] = ([a^{c}])^{k} = [a^{ck}] = [a^{\phi(n)}]
>$$

[Corollario - Piccolo teorema di Fermat]
Sia $p$ un numero primo e $a \in \mathbb{N}$. Allora in $\mathbb{Z}_{p}$ abbiamo che $[a] = [a^{p}]$.

>[!note]- Dimostrazione
>Se $p$ è primo si ha che $\phi(p) = p -1$. Allora dal teorema di Eulero segue che se $a \neq 0$ e $p \cancel{ |}a$, $a^{\phi(p)} \equiv [1]_{p}\implies a^{p-1}\equiv [1]_{p} \implies a^{p} \equiv [a]_{p}$. 
>Se $a = 0$ o $p |a$ l'uguaglianza si riduce a $[0] =[0]$
### Endomorfismo

Siano $v,w$ spazi vettoriali su un [[Campo]] $K$, un funzione $f:v\to w$ è un morfismo di spazi vettoriali se
$$
f(av_{1} + bv_{2}) = af(v_{1}) + b f{(v_{2})}
$$
Un morfismo di campi vettoriali è detto un **endomorfismo** di $v$. L'insieme degli endomorfismi di uno spazio vettoriale è indicato con $End(v)$. Questo insieme è un anello con le operazioni di somma e composizione di funzioni, ed ha come identità $Id_{v}: V\to V$ -- se $d\mathrm{Im} v >1$ allora l'anello è anche commutativo.

Un endomorfismo invertibile è anche detto **automorfismo**.

Ad un endomorfismo $f \in End(v)$, se $di m(v) = n$, possiamo associare una matrice. Sia $\{ e_{1},\dots,e_{n}  \}$ una base di $v$. Sia 
$$
f(e_{i}) = a_{1i}e_{1} + \dots + a_{ni}e_{n}
$$
allora ad $f$ associamo la matrice $M(f)\in Mat_{n\times n}(K)$ la cui colonna $i$-esima è $(a_{1i}, \dots, a_{ni})^{T}$

[Teorema]
Sia $v$ uno spazio vettoriale di dimensione $n$ sul campo $K$. Allora la funzione
$$
M: End(v) \to Mat_{n\times n}(K) \qquad f\to M(f)
$$
è un isomorfismo di anelli.

>[!example]
>Si consideri il campo $\mathbb{F}_{4} = \mathbb{F}_{2}[X] / \left< 1 + x + x^{2} \right>$. Questo è uno spazio vettoriale di dimensione $2$ sul campo $\mathbb{F}_{2}$. Nella base $\{ 1, x \}$, l'automorfismo di Frobenius $\Phi: \mathbb{F}_{4} \to \mathbb{F}_{4} \equiv v \to v^{2}$, che è un morfismo di spazi vettoriali perché $\Phi(y)=y$, è rappresentato con una matrice $Mat_{2\times2}$. 
>Le colonne si trovano come descritto sopra con la base canonica $\Phi(e_{1}) = \Phi(1) = 1$ e $\Phi(e_{2}) = \Phi(x)=x^{2}= 1+x$ quindi
>$$
>M(\Phi) = \begin{pmatrix}
>1 & 1 \\
>0 & 1
\end{pmatrix}
>$$
>La rappresentazione matriciale di $Aut(\mathbb{F}_{4}) \simeq \{A\in Mat_{2\times 2} (\mathbb{F}_{2}) :  \det(A) = 1\}$ e ce ne sono $16$
>$$
>\left\{\begin{pmatrix}
>1 & 0 \\
>0 & 1
\end{pmatrix}, \begin{pmatrix}
>1 & 1 \\
>0 & 1
\end{pmatrix}, \dots
> \right\} 
>$$
>Ma il campo è composto solo da 
>$$ Aut(\mathbb{F}_{4}) \underbrace{ = }_{ \text{ come campo } } 
>\left\{\underbrace{ \begin{pmatrix}
>1 & 0 \\
>0 & 1
\end{pmatrix} }_{ M(\Phi) }, \underbrace{ \begin{pmatrix}
>1 & 1 \\
>0 & 1
\end{pmatrix} }_{ M(\phi)^{2} }
> \right\} 
>$$

Sia $v$ uno spazio vettoriale di dimensione $n$ su un campo $K$. Sia $\{ e_{1},\dots,e_{n} \}$ una base di $v$. L'insieme 
$$
V^{*} = \{ f: V \to K  : f \text{ è morfismo di spazi vettoriali}\}
$$
è detto **spazio duale** di $v$. Sia $e_{i}^{*}: V\to K$ il morfismo definito da 
$$
e_{i}^{*}(e_{j}) = \begin{cases}
1_{K}  & i = j \\
0  & \text{altrimenti}
\end{cases}
$$
L'insieme $\{ e_{1}^{*},\dots,e_{n}^{*} \}$ è una base di $V^{*}$. In particolare $dim(V^{*})=dim(V)=n$