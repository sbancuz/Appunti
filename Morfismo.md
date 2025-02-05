---
tags:
  - logica_algebra
---
Siano $M_{1}, M_{2}$ monoidi con [[Identità]] $e_{1},e_{2}$. Una funzione $f:M_{1} \to M_{2}$ è un **morfismo di monoidi** se
1) $f(e_{1}) = e_{2}$
2) $f(xy) = f(x)f(y)$

Il **nucleo** di un morfismo di monoidi $f:M_{1} \to M_{2}$ è il [[Monoide#Sottomonoide]] di $M_1$ definito così
$$
Ker(f) = \{ x \in M : f(x) = e_{2} \}
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
>Ker(\phi) = \{ [g] \in G_{1} /Ker(f) : \phi([g]) = 0_{2} \} = \{ [g] \in G_{1} /Ker(f) : f(g) = 0_{2} \} = \{ [0_{1}] \}
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
---



