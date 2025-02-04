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