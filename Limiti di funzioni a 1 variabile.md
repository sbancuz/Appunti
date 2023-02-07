	Sia $f$ una funzione definita su un sottoinsieme da $R\to R$, sia poi $c$ un punto di accumulazione per $f$, cioè $c\in R$ ed esiste un intervallo $c\in I$ tale che $f$ $\forall {x} \in {I}$ tranne eventualmente in c.

Per estensione c può anche essere $\infty \lor -\infty$ purché l'intervallo permetta.

Poiché $c\in R \cup\{+\infty,-\infty\}$ di sicuro esistono delle successioni $\{{x_{n}}\}_{n\in N}$ tali che $\lim_{ n \to \infty } {x_{n}}=c$. In corrispondenza della successione $\{{x_{n}}\}_{n\in N}$ si può considerare la successione $\{{f(x_{n})}\}_{n\in N}$ 

Allora possiamo passare la limite di successioni al limite di funzioni in questo modo:

### Definizione successionale di limite

Sia $f$ una funzione e $c$ un punto di accumulazione per $f$, se per ogni successione $\{{x_{n}}\}_{n\in N}$ tale che $\lim_{ n \to \infty } {x_{n}}=c$ si ha che $\lim_{ n \to \infty } {f(x_{n})}=l$, allora si dice che il limite per $x$ che tende a $c$ di $f(x)=l$ e si scrive $$
\lim_{ x \to c } {f(x)}=l
$$
Se $f$ è tale che $\lim_{ x \to c } {f(x)}=0$ si dice che $f$ è infinitesima per $x\to c$ 
se $\lim_{ x \to c } {f(x)}=\infty$ si dice che $f$ è infinitesima per $x\to c$

## Teorema di unicità del limite

Se esiste $\lim_{ x \to c } {f(x)}$, allora il limite è unico.

>[!note]- Dimostrazione
>Siano $l_{1},l_{2}$ tali che $\lim_{ x \to c } {f(x)}=l_{1}$ e $\lim_{ x \to c } {f(x)}=l_{2}$, allora esisterebbe una successione $\{{x_{n}}\}_{n\in N}$ tale che $\lim_{ n \to \infty } {x_{n}}=c$ e $\lim_{ n \to \infty } {f(x_{n})}=l_{1}$ e  $\lim_{ n \to \infty } {f(x_{n})}=l_{2}$ e per l'unicità delle successioni $l_{1}=l_{2}$

## Teorema del confronto

Siano $f,g,h$ definite per $x\to c$ con $c\in R\cup\{-\infty,\infty\}$ tale che $\lim_{ x \to c } {f(x)}=\lim_{ x \to \infty } {h(x)}=l$ con $l\in R\cup\{-\infty,\infty\}$ e definitivamente per $x\to c$ si abbia $f(x)\leq g(x)\leq h(x)$ allora $\lim_{ x \to c } {g(x)}=l$

>[!note]- Dimostrazione
>Ci riconduciamo al teorema del contronto delle successioni.
>Siano $\{{x_{n}}\}_{n\in N}$ una successione tale che $\lim_{ n \to \infty } {x_{n}}=c$, provo che $\lim_{ n \to \infty } {g(x_{n})}=l$.
>
>D'altra parte per ogni $n$, $f(x_{n})\leq g(x_{n})\leq h(x_{n})$ e inoltre $\lim_{ n \to \infty } {f(x_{n})}=l,\lim_{ n \to \infty } {h(x_{n})}=l$ siamo nelle ipotesi del teorema del confronto per successioni quindi $\lim_{ n \to \infty } {g(x)}=l$

### Corollario

Se $\lim_{ x \to 0 } {g(x)}=0$ e definitivamente per $x\to c$ si ha $|f(x)| \leq g(x)$, allora $\lim_{ x \to c } {f(x)}=0$

### Corollario

Se $\lim_{ x \to 0 } {f(x)}=0$ e $g(x)$ è definitivamente limitata per $x\to c$ allora $\lim_{ x \to c } {(f(x)g(x))}=0$

## Teorema di permaneza del segno

Se $\lim_{ x \to c } {f(x)}=l$ e definitivamente per $x\to c$ si ha $f(x)\geq 0$ allora $l\geq 0$

### Corollario

Se $\lim_{ x \to c } {f(x)}=l$ e $l\geq 0$, allora definitivamente per $x\to c$ si ha $f(x)>0$

### Corollario

Se $f$ è continua in $c$ e $f(c)>0$ allora definitivamente per $x\to c$ si ha $f(x)>0$

## Tipi di limite

Sia $\lim_{ x \to c } {f(x)}=l$ 

Il limite è finito se $l \in R$
Il limite è infinito se $l \in \{-\infty, \infty\}$
Il limite è al finito se $c \in R$
Il limite è all'infinito se $c \in \{-\infty,\infty\}$

### Limiti per eccesso e per difetto

Sia $\lim_{ x \to c } {f(x)}=l$  con $c \in \{-\infty,\infty\}$ e $l \in R$ si dice che $f \to l$ per eccesso per $x\to c$ se per ogni successione $\{{x_{n}}\}_{n\in N}$ tale che $\lim_{ n \to \infty } {x_{n}}=c$ si ha che $f(x_n)$ tende a $l$ per eccesso per $n\to \infty$ e definitivamente $f(x_{n})\geq l$. 
In tal caso di scrive che $$
\lim_{ x \to c } {f(x)}=l^+
$$
Se invece definitivamente $f(x_{n})\leq l$ allora $$
\lim_{ x \to c } {f(x)}=l^-
$$
### Limiti destri e sinistri

Sia $f$ una funzione con $c \in R$ e $l \in R \cup\{-\infty,\infty\}$ si dice che $f(x)\to l$ per $x\to c$ da destra se per ogni successione $\{{x_{n}}\}_{n\in N}$ tale che $\lim_{ x \to \infty } {x_{n}}=c^+$ si ha che $\lim_{ n \to \infty } {f(x_{n})}=l$ e si scrive $$
\lim_{ x \to c^+ } {f(x)}=l
$$
Se invece arriva da sinistra si scrive $$
\lim_{ x \to c^- } {f(x)}=l
$$
## Definizione topologica di limite

Sia $c \in R\cup\{-\infty,\infty\}$ e $f$ definita difinitivamente per $x\to c$ si dice che $\lim_{ x \to c } {f(x)}=l$ con $l \in R\cup\{-\infty,\infty\}$ se per ogni intorno $I_{l}$ di $l$ esiste un intorno $J_{c}$ di $c$ tale che $$
\forall {x} \in {J_{c}},x\neq c \text{ si ha che } f(x)\in I_{l} 
$$
è una definizione compatta che riassume tutti i casi possibili.

### Finito al finito

Siano $c,l\in R$ gli intorni sono intervalli centrati in $c,l$ e abbiamo $\lim_{ x \to c } {f(x)}=l$ sse $$
\forall {\epsilon} > {0},\exists {\delta} > {0} \text{ | } |x-c|<\delta,x\neq c \text{ si ha } |f(x)-l|<\epsilon  
$$
### Finito all'infinito

Siano $c\in R,l=+\infty$ allora $\lim_{ x \to c } {f(x)}=+ \infty$ sse $$
\forall {M} > {0},\exists {\delta} > {0} \text{ | } |x-c|<\delta,x\neq c \text{ si ha } f(x) > M
$$
Siano $c\in R,l=-\infty$ allora $\lim_{ x \to c } {f(x)}=- \infty$ sse $$
\forall {m} < {0},\exists {\delta} > {0} \text{ | } |x-c|<\delta,x\neq c \text{ si ha } f(x) < m
$$
## Infinito al finito

Siano $c=+\infty, l\in R$ allora $\lim_{ x \to \infty } {f(x)}=l$ sse $$
\forall {N} > {0},\exists {M} > {0} \text{ | } x>M \text{ si ha } f(x)>N  
$$
Siano $c=-\infty, l\in R$ allora $\lim_{ x \to -\infty } {f(x)}=l$ sse $$
\forall {N} > {0},\exists {M} > {0} \text{ | } x<-M \text{ si ha } f(x)>N  
$$
## Asintoti 

### Orizzontali

Sia $f$ una funzione definita in un intorno di $\pm\infty$, si dice che $f$ ha un asintoto orizzontale di equazione $y=l$ per $x\to \pm\infty$ se $\lim_{ x \to \pm\infty } {f(x)}=l$ con $l\in R$

### Obliqui

Sia $f$ una funzione definita in un intorno di $\pm\infty$, si dice che $f$ ha un asintoto orizzontale di equazione $y=mx+x$ con $m\neq 0,m\in R$ per $x\to \pm\infty$ se $\lim_{ x \to \pm\infty } {f(x)}=\pm \infty$ se $$
\lim_{ x \to \infty } {(f(x)-(mx+q))}=0
$$
Dove $m=\lim_{ x \to \infty } {\frac{f(x)}{x}}$ e $q=\lim_{ x \to \infty } {f(x)-mx}$

### Verticali

Sia $c\in R$ di accumulazione per $f$, si dice che la retta verticale $x=c$ è asintoto verticale per $f$ per $x\to c$ se $\lim_{ x \to c^\pm } {f(x)}=\pm \infty$

## Continuità

Sia $f:I\to R$ con $I$ intervallo e $c\in I$ si dice che $f$ è continua in c sse $$
\lim_{ x \to c } {f(x)}=f(c)$$
>[!warning]
>Per essere continua in $c$, $f$ deve essere definita in $c$.
>Se il limite esiste allora sia $g(x)$ l'estensione di $f$ continua in $c$

La continuità può anche essere solo da destra o sinistra

>[!info]
>Se $f:[a,b)\to R$, dico che $f$ è continua in $a$ se è continua da destra, in $b$ da sinistra

Siano $f,g$ funzioni continue in $c$ allora
	1. $\forall {a,a_{1}} \in {R}, af(x)+a_{1}g(x)$ è continua in $c$
	2. $f(x)g(x)$ è continua in $c$
	3. $\frac{f(x)}{g(x)}$ è continua in $c$ purché $g(c)\neq 0$

### Teorema

Sono continue nel loro dominio:
	1. Tutte le funzioni del tipo $f(x)=x^a$
	2. Tutte le funzione $a^x$ e $\log_{a}x$ con $a>0$ e $a\neq 1$
	3. $\sin x$ e $\cos x$
	
Segue quindi la continuità di ogni funzione polinomiale

## Teorema del cambiamento di variabile

Siano $f,g$ funzioni tali che risulti definita la composizione $f(g(x))$ definitivamente per $x\to c$ con $c\in R\cup\{-\infty,\infty\}$ e inoltre valgono:
	1. $\lim_{ x \to c } {g(x)}=d$
	2. esiste $\lim_{ t \to d } {f(t)}\in R\cup\{-\infty,\infty\}$
	3. $g(x)\neq d$ definitivamente per $x\to c$

Allora $$
\lim_{ x \to c } {f(g(x))}=\lim_{ t \to d } {f(t)}
$$
### Corollario

Sia $g$ funzione continua definita in un intorno di $c$ e $f$ definita e continua in un intorno di $g(c)$ allora $f(g(x))$ sarà definita e continua in $c$

