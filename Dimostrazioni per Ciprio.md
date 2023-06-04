---
tags: [analisi_1]
---

### Teorema di convergenza delle successioni monotone limitate in $\mathbb{R}$

Sia $x_{n}\in \mathbb R$ una successione di numeri reali monotona crescente quindi
$$
\forall {n} \geq {0} \implies x_{n}\leq x_{n+1} 
$$
e superiormente limitata che vuol dire
$$
\exists {M} \in {\mathbb R} \text{ tc } x_{m}\leq M \text{  } \forall {m} \geq  {0}   
$$

Allora $\{x_{n}\} \subset \mathbb R$ è di Cauchy e quindi convergente cioè
$$
\exists {\lim_{ n \to \infty } {x_{n}}} \in {\mathbb R} 
$$

#### Dimostrazione

Per la completezza di $\mathbb R$ è sufficiente mostrare che la successione $x_{n}$ sia di Cauchy. Cioè
$$
\forall {\epsilon} > {0}, \exists {N(\epsilon)} \geq {0} \text{ | }  n,m \geq N(\epsilon) \implies |x_{n}-x_{m}| < \epsilon
$$
Per assurdo supponiamo che la successione $\{X_{m}\}$ non abbia questa proprietà. Quindi 
$$
\exists {\epsilon} > {0} \text{ | } \forall {N} \geq {1}, \exists {m_{N},n_{N}} \geq  {N} \text{ tc } |x_{m_{N}}-x_{n_{N}}| \geq \epsilon   
$$

Possiamo assumere che il punto $x_{m_{N}}\geq x_{n_{N}}$ così $x_{m_{N}}\geq \epsilon+x_{n_{N}}$ 
Per $N_{1}=1, \exists {m_{1}>n_{1}} \text{ tc } x_{m_{1}} \geq \epsilon x_{n_{1}}$
Per $N_{2}=m_{1}, \exists {m_{2}>n_{2}\geq N_{2} = m_{1}>n_{1}}$
	
Allora avremo che $x_{n_{2}}\geq 2\epsilon +x_{m_{1}}$ e più in generale
$$
X_{K+1}=m_{k}>n_{k}, \exists {m_{k+1}>n_{k+1}} >N_{k+1}>m_{k}>n_{k}>\dots>k\epsilon+x_{n_{1}} 
$$
Per la monotonia del limite non esiste
$$
\lim_{ n \to \infty } {x_{m_{k+1}}} \geq \lim_{ k \to \infty } {k\epsilon+x_{n_{1}}} = \infty
$$
e quindi $\{x_{n}\}$ è di Cauchy.

____

### Esistenza di SUP e INF in $\mathbb R$

Se $A\subseteq \mathbb R$ è superiormente limitato, cioè ha almeno un maggiorante, allora $\exists {\sup A} \subseteq {\mathbb R}$

#### Dimostrazione

Poiché $A$ è superiormente limitato possiamo dire che $\exists {b_{0}} \in {\mathbb R} \text{ tc }\forall x\in A \implies x \leq b_{0}$  

Sia ora $a_{0}\in A$ fissato, avremo che $[a_{0},b_{0}]\cap A\neq 0$.
Consideriamo il punto medio $c = \frac{a_{0}+b_{0}}{2}$ e consideriamo $[a_{0},c],[c,b_{0}]$ in cui in almeno una delle 2 metà vi saranno punti di $A$.

Consideriamo tra le due metà quella più a destra che contiene punti di $A$ con $[a_{1},b_{1}]$ e $b_{1}$ è maggiorante di $A$. 

Ripeto il procedimento per dicotomia.

Quello che ottengo è una successione decrescente di intervalli tale che $b_{n}$ è maggiorante di $A$.

${a_{n}}$ è crescente e superiormente limitata da $b_{0}$ invece ${b_{n}}$ è decrescente e inferiormente limitata da $a_{0}$.

Allora per il teorema di convergenza delle successioni monotone limitate 
$$
\exists {\lim_{ n \to \infty } {a_{n}}} = \exists {\lim_{ n \to \infty } {b_{n}}} =\overline{x} \in \mathbb  R, \exists {\lim_{ n \to \infty } {(b_{n}-a_{n})}} =\lim_{ n \to \infty } {\frac{b_{0}-a_{0}}{2^{n}}} = 0
$$
Infatti mostriamo che $\overline{x}$ è estremo superiore di $A$, infatti $\forall {x} \in {A}$ fissato $x\leq b$ passando al limite
$$
\forall {x} \in {A}\implies x=\lim_{ n \to \infty } {x}\leq \lim_{ n \to \infty } {b_{n}}=\overline{x} 
$$
Cioè $\overline{x}$ è maggiorante di $A$. Rimane da mostrare che $\overline{x}$ sia il più piccolo maggiorante.

Sia $\epsilon>0$ e consideriamo $\overline{x}-\epsilon<\overline{x}$. Poiché $\overline{x}=\lim_{ n \to \infty } {a_{n}},\exists {n} \geq {1} \text{ tc } \overline{x}-\epsilon<a_{n}\leq \overline{x}$.
Ma poiché $[a_{n},b_{n}]\cap A\neq 0 \implies \overline{x}-\epsilon$ non è maggiorante.

_____


### Proprietà di Bolzano Weiestrass

Sia $E \subseteq \mathbb R$ limitato e infinito (Reale), allora $\exists {}  {}$ almeno un punto di accumulazione quindi $E'\neq 0$.

#### Dimostrazione
 
Visto che $E$ è limitato, quindi è contenuto in un intervallo $E\subseteq[a_{0},b_{0}]$. Sia $c=\frac{a_{0}+b_{0}}{2}$il punto medio e consideriamo adesso $[a_{0},c], [c,b_{0}]$ in cui in almeno una delle 2 vi sono infiniti punti.
Scelgo una delle 2 metà che contiene infiniti punti di $E$ e la chiamo $[a_{1},b_{1}]$. 

Facendo per dicotomia otteniamo una successione descrescente di intervalli 
$$
[a_{n+1},b_{n+1}]\subset[a_{n},b_{n}]\subset\dots[a_{0},b_{0}]
$$
tali che ogni intervallo abbia cardinalità infinita.

${a_{n}}$ è crescrente e superiormente limitata da $b_{0}$ invece ${b_{n}}$ è decrescrente e inferiormente limitata da $a_{0}$
$$
\lim_{ n \to \infty } {(b_{n}-a_{n})= \lim_{ n \to \infty } {\frac{b_{0}-a_{0}}{2^{n}}}=0}\implies \exists {\lim_{ n \to \infty } {a_{n}}} , \exists {\lim_{ n \to \infty } {b_{n}}} = \overline{x}  
$$

Scegliamo $x_{n}\in E\cap[a_{n},b_{n}]$ con $x_{n}\neq \overline{x}$, e possiamo farlo poiché in quell'intervallo vi sono infiniti punti di $E$. Quindi
$$
\lim_{ n \to \infty } {a_{n}}\leq \lim_{ n \to \infty } {x_{n}}\leq \lim_{ n \to \infty } {b_{n}} \implies \overline{x} = \lim_{ n \to \infty } {x_{n}}
$$
$\overline{x}$ sarà sicuramente punto di accumulazione.

____

### Teorema di Weiestrass / Esistenza max/min per funzioni continue

Sia $f$ continua in $[a,b]$ allora ammette massimo e minimo assoluti nell'intervallo $[a,b]$, quindi 
$$
\forall {x} \in {[a,b]}, \exists {x_{m}, x_{M}} \in {[a,b]} \text{ tc } m= f(x_{m})\leq f(x) \leq f(x_{M})= M 
$$

#### Dimostrazione

Sia $M=\sup Im(f)\in \mathbb R \cup\{+\infty\}$. Per le proprità del $\sup$ $\exists \{y_{n}\} \subset \mathrm{Im}(f) {}$ convergente ad M
$$
\lim_{ n \to \infty } {y_{n}}=M
$$
Se per un certo $m$ si ha $y_{m}=M$ allora $M=\max\mathrm{Im}(f)$ e la dimostrazione termina.

Ma se questo non vale, allora possiamo supporre che $y_{n}\neq y_{m}$ se $n\neq m$. 
Quindi $\exists \{x_{n}\} \in {[a,b]} \text{ tc } y_{n}=f(x_{n}), \forall {n}  {}$, di conseguenza $n\neq m\implies x_{n}\neq x_{m}$ e quindi
$$
\{x_{n}\}\subset[a,b]\text{ è un insieme limitato e infinito}
$$

Per il teorema di Bolzano-Weiestrass $\{x_{n}\}$ ammette un punto $x_{M}\in[a,b]$ di accumulazione. Quindi
$$
\exists \{x_{nk}\}_{k}\subset\{x_{n}\} \text{ convergente a } x_{M} : \lim_{ k \to \infty } {x_{nk}}=x_{M}  
$$

Allora $M=\lim_{ n \to \infty } {y_{n}} = \lim_{ k \to \infty } {y_{nk}} = \lim_{ k \to \infty } {f(x_{nk})}$ e poiché $f$ è continua ho che $f(\lim_{ k \to \infty } {x_{nk}})$
$$
M=f(x_{M}) \in \mathbb R \implies M=\max \mathrm{Im}(f)
$$

----

### Teorema degli zeri

Sia $f$ continua in $[a,b]$ tale che 
$$
f(a)f(b) < 0
$$
cioè ammette segno opposto agli estremi del sistema.
$\exists {x_{0}} \in {(a,b)}$ dove $f$ si annulla in $f(x_{0}) = 0$

#### Dimostrazione

Poniamo $a_{0}=a$, $b_{0}=b$  allora consideriamo il punto medio $c = \frac{a_{0}+b_{0}}{2}$
Se $f(c) = 0$ la dimostrazione è fatta, se no considero $[a_{0},c]$ e $[c,b_{0}]$ e consideriamo quella a cui estremi si hanno segni opposti e la denotiamo con $[a_{1},b_{1}]$ e ripeto per dicotomia.

Iterando se $f\left( \frac{a_{n}+b_{n}}{2} \right) = 0$ la dimostrazione termina, altrimenti abbiamo una successione decrescente di intervalli tale che 
$$
[a_{n+1},b_{n+1}] \subset [a_{n},b_{n}] \subset \dots \subset [a_{0},b_{0}] \text{ con } \forall {n}  {} f(a_{n}) f(b_{n})<0
$$
E per la dicotomia si ha che
$$
\exists {\lim_{ n \to \infty } {a_{n}}} =\lim_{ n \to \infty } {b_{n}} = x_{0} \in [a_{0},b_{0}] 
$$
e quindi si ha anche che 
$$
\lim_{ n \to \infty } {f(a_{n})f(b_{n})} = 0
$$
Per la continuità di $f$ in $x_{0}$ si ha che
$$
f(\lim_{ n \to \infty } {a_{n}})f(\lim_{ n \to \infty } {b_{n}}) \leq 0 \implies f(x_0)f(x_0)\leq 0 \implies f(x_{0}) = 0
$$

----

### Teorema dei valori intermedi

Sia $f$ continua in $[a,b]$ allora ammette massimo e minimo assoluti nell'intervallo $[a,b]$, quindi 
$$
\forall {x} \in {[a,b]}, \exists {x_{m}, x_{M}} \in {[a,b]} \text{ tc } m= f(x_{m})\leq f(x) \leq f(x_{M})= M 
$$
allora 
$$
\forall {\lambda} \in {(m,M)}, \exists {x_{\lambda}}\in [a,b] \text{ tc } f(x_\lambda) = \lambda  
$$
cioè $\mathrm{Im}(f)=[m,M]$ e quindi la funzione assume tutti i valori in $[m,M]$

#### Dimostrazione

Supponiamo $x_{m}<x_{M}$ e applico il teorema degli zeri, allora si ha che
$$
g:[x_{m},x_{M}] , g(x)=f(x) - \lambda
$$
allora $g$ è continua in $[x_{m}, x_{M}]$ e in più si ha
$$
g(x_{m}) = f(x_{m})- \lambda < 0 \text{ e }  g(x_{M}) = f(x_{M})- \lambda > 0 \implies g(x_{m})g(x_{M}) < 0
$$
quindi $\exists {x_{\lambda}} \in {(x_{m}, x_{M})}$ tc $0 = g(x_{m}) = f(x_{m}) - \lambda \implies f(x_{m}) = \lambda$ 

---

### Continuità delle funzioni derivabili

Sia $f:(a,b) \to \mathbb R$ e derivabile in $x_{0} \in (a,b)$ allora $f$ è continua in $x_{0}$

#### Dimostrazione

$$
\lim_{ x \to x_{0} } {(f(x)-f(x_{0}))} = \lim_{ x \to x_{0} } \frac{{f(x)-f(x_{0})}}{(x-x_{0})}(x-x_{0})=\lim_{ x \to x_{0} } \frac{{f(x)-f(x_{0})}}{(x-x_{0})}\lim_{ x \to x_{0} } {(x-x_{0})}=0
$$

----

### Lemma di Fermat

Sia $f:(a,b) \to \mathbb R$ e sia $x_{0}\in(a,b)$ un punto di estremo di $f$. Se $f$ è derivabile in $x_{0}$ allora 
$$
f'(x_{0}) = 0
$$
I punti dove si annulla $f'$ sono detti stazionari o critici

#### Dimostrazione

Sia $x_{0}\in (a,b)$ massimo di $f$ in $(a,b)$ quindi
$$
\forall {x} \in {(a,b)} \implies f(x)\leq f(x_{0})
$$
Se $x>x_{0}$ si ha $\frac{f(x)-f(x_{0})}{x-x_{0}}\leq 0$
Per la permanenza del segno ho che
$$
\lim_{ x \to x_{0}^{+} } {\frac{f(x)-f(x_{0})}{x-x_{0}}\leq 0}
$$
Se $x<x_{0}$ si ha $\frac{f(x)-f(x_{0})}{x-x_{0}}\geq 0$
Per la permanenza del segno ho che
$$
\lim_{ x \to x_{0}^{-} } {\frac{f(x)-f(x_{0})}{x-x_{0}}\geq 0}
$$
Quindi si deduce che 
$$
\begin{cases}
f'(x)\geq 0 \\
f'(x)\leq 0
\end{cases} \implies f'(x) = 0
$$
----

### Teorema di Lagrange

Sia $f$ continua in $[a,b]$ derivabile in $(a,b)$ allora
$$
\exists {c} \in {(a,b)} \text{ tc }\frac{ f(b)-f(a)}{b-a} = f'(c) 
$$
In generale i punti di Lagrange non sono unici

#### Dimostrazione

Consideriamo 
$$
g:[a,b]\to \mathbb R \implies g(x)=f(a)+\frac{f(b)-f(a)}{b-a}(x-a)
$$
Il cui grafico è una retta e in cui $g(a) = f(a)$ e $g(b)=f(b)$. Ovvero sarà la retta passante per $(a,f(a))$ e $(b, f(b))$ con coefficiente angolare $\frac{f(b)-f(a)}{b-a}$

$g$ è continua e derivabile in $\mathbb R$ e $g'(x) = \frac{f(b)-f(a)}{b-a}$

Considero adesso $h=f-g$ su $[a,b]$, questa funzione sarà continua su $[a,b]$ e derivabile su $(a,b)$. 

Per il teorema di Weiestrass $\exists {x_{m},x_{M}} \in {[a,b]}$ di estremo globale

**Primo caso** => $x_{m},x_{M}$ sono agli estremi di $[a,b]$
$$
\forall {x}\in  {}[a,b] \implies
\begin{cases}
h(a) = f(a) - g(a) = 0 \\
h(b) = f(b) - g(b) = 0 
\end{cases} 
$$
cioè $0 = h(x) \implies f(x) = g(x) \implies f'(x) = g'(x) = \frac{f(b)-f(a)}{b-a}$ che verifica il teorema $\forall {c}\in  {}(a,b)$

**Secondo caso** => almeno uno tra $x_{m}, x_{M} \in (a,b)$, per esempio $x_{M}$.
Applico quindi il lemma di Fermat
$$
h'(x_{M}) = 0 = f'(x_{M})-g'(x_{M}) = \frac{f(b)-f(a)}{b-a}
$$
e quindi è verificato il teorema con $c=x_{M}$

---

### Test di monotonia

Sia $f:(a,b) \to \mathbb R$ derivabile in $(a,b)$ allora:
	- $f$ è crescente <=> $f'(x) >0, \forall {x} \in {(a,b)}$ 
	- $f$ è decrescente <=> $f'(x) <0, \forall {x} \in {(a,b)}$ 

#### Dimostrazione

Sia $f$ crescente allora
$$
\frac{f(y)-f(x)}{y-x}\geq 0 \text{ se }a<x<y<b
$$
e per la permanenza del segno ho che 
$$
f'(x)=\lim_{ y \to x } \frac{{f(y)-f(x)}}{y-x}\geq 0 
$$

----

### Teorema di de L'Hopital

Siano $f,g:(a,b)\to \mathbb R$ derivabili e infinitesime con $g\neq 0$ allora si ha che 
$$
\exists	\lim_{ x \to a^{+} } {\frac{f'(x)}{g'(x)}}= l \implies \exists \lim_{ x \to a^{+} } {\frac{f(x)}{g(x)}} = l
$$

#### Dimostrazione

Definiamo $f(a)=g(a)= 0$ e le enstendo in maniera continua a $[a,b)$.

Fisso adesso $x\in(a,b)$
Abbiamo che $f,g$ sono continue in $[a,x]$ e derivabili in $(a,x)$ poiché $f,g$ derivabilii in $(a,b)$

Applico il teorema di Lagrange ad $h:[a,x]\to \mathbb R$ definita
$$
\forall {y} \in {[a,x]}, h(y)=f(x)g(y) -f(y)g(x)
$$
Quindi $\exists {y(x)} \in {(a,x)} \text{ tc } \frac{h(x)-h(a)}{x-a} = h'(g(x)) = 0$
$$
\frac{d}{dx}h(x) = f(x)g'(y(x)) - f'(y(x))g(x) \implies \frac{f(x)}{g(x)} = \frac{f'(y(x))}{g'(y(x))}
$$
quindi ho che
$$
\lim_{ x \to a^{+} } {\frac{f(x)}{g(x)}} = \lim_{ x \to a^{+} } {\frac{f'(y(x))}{g'(y(x))}}
$$
che per il teorema del limite della funzione composto diventerà
$$
\lim_{ y \to a^{+} } {\frac{f'(y)}{g'(y)}} = l
$$

---

### Teorema di Taylor con resto di Peano

Sia $f:(a,b)\to \mathbb R$ derivabile n-volte in $x_{0}\in(a,b)$. Definiamo il suo polinomio di Taylor di ordine n in $x_{0}$ come 
$$
T^{f}_{n,x_{0}} (x) = \sum_{k=0}^{n} \frac{f^{k}(x_{0})}{k!} (x-x_{0})^{k}
$$

allora $\exists {}  {}$ una funzione di resto di ordine n, in cui $x_{0}$
$$
R^{f}_{n,x_{0}}:(a,b)\to \mathbb R \implies f(x) = T_{n,x_{0}}^{f}(x)+ R_{n,x_{0}}^{f}(x)
$$
ed il resto è infinitesimo di ordine maggiore di n 

#### Dimostrazione

Definisco $R_{n,x_{0}}^{f}(x) = f(x) - T_{n,x_{0}}^{f}(x)$

Uso quindi de L'Hopital
$$
\lim_{ x \to x_{0} } \frac{{ f(x) - T_{n,x_{0}}^{f}(x)}}{(x-x_{0})^{n}} = \lim_{ x \to x_{0} } \frac{{ f'(x) - (T_{n,x_{0}}^{f})'(x)}}{n(x-x_{0})^{n-1}} = \lim_{ x \to x_{0} } \frac{{ f'(x) - ( \sum_{k=0}^{n} \frac{f^{k}(x_{0})}{(k-1)!} (x-x_{0})^{k-1}}}{n(x-x_{0})^{n-1}} 
$$
Applico n-1 volte de L'Hopital
$$
\lim_{ x \to x_{0} } \frac{{f^{n-1}(x)-(f^{n-1}(x_{0})+f^{n}(x_{0})(x-x_{0}))}}{n!(x-x_{0})} = \frac{1}{n!}\lim_{ x \to x_{0} } \left[ \frac{{f^{n-1}(x)-f^{n-1}(x_{0})}}{x-x_{0}} -f^{n}(x_{0})\right] = 0
$$

---

### Primo teorema fondamentale del calcolo integrale

Sia $f:[a,b]\to R$ una funzione continua, allora se $F$ è una primitiva di $f$ allora 
$$
\int_{a}^{b} f(x) \, dx =F(b)-F(a)
$$

### Dimostrazione

$F(b)-F(a)=F(x_{n})-F(x_{0})=F(x_{n})-F(x_{n-1})+F(x_{n-1})-F(x_{n-2})+\dots$

Allora $\sum_{i=0}^{x-1}(F(x_{i+1})-F(x_{i}))$ è continua e derivabile in $[a,b]$ e per il teorema di Lagrange si ha che $$\frac{F(x_{i+1})-F(x_{i})}{x_{i+1}-x_{i}}=F'(z_{i})=f(z_{i})$$

Cioè $F(x_{i+1})-F(x_{i})=f(z_{i})(x_{i+1}-x_{i})$

Allora $F(b)-F(a)=\sum_{i=0}^{n-1}f(z_{i})(x_{i+1}-x_{i})$ che è la somma di C-R, passando al limite $$F(b)-F(a)=\lim_{ n \to \infty } \sum_{i=0}^{n-1}f(z_{i})(x_{i+1}-x_{i})=\int_{a}^{b} f(x_{}) \, dx $$

---
### Secondo teorema fondamentale del calcolo integrale

Sia $f:[a,b]\to R$ una funzione continua in $[a,b]$ e sia  $x_{0}\in[a,b]$, sia poi 
$$
F(x)=\int_{x_{0}}^{x} f(t)  \, dt
$$
Allora $F(x)$ è detta funzione integrale di $f(x)$ e $F(x)$ è una funzione continua e derivabile in $[a,b]$ e $\forall {x} \in {[a,b]}$ si ha $F'(x)=f(x)$

### Dimostrazione
$F'(x)=\frac{F(x+h)-F(x)}{h}=\frac{1}{h}\left( \int_{x}^{x+h} f(t)  \, dt-\int_{x+h}^{x} f(t)  \, dt \right)=\frac{1}{h}\int_{x}^{x+h} f(t)\, dt$
Per il teorema del valor medio integrale $\frac{F(x+h)-F(x)}{h}=f(z)$ con $z\in[x,x+h]$
Passando al limite per $h\to{0}$ dove $z\to x$ dunque
$$F'(x)=\lim_{ h \to 0 } {\frac{F(x+h)-F(x)}{h}}=\lim_{ z \to x } {f(z)}=f(x)$$

---

### Criterio della radice

Sia $\{{a_{n}}\}_{n\in N}$ una successione non negativa, se esiste il $\lim_{ n \to \infty } {\sqrt[n]{ a_{n} }}$ allora 
	• se $l<1$, $\sum_{i=0}^\infty{a_{i}}$ converge
	• se $l>1$, $\sum_{i=0}^\infty{a_{i}}$ diverge
	• se $l=1$ non si sa

### Dimostrazione
Sia $\lim_{ n \to \infty } {\sqrt[n]{ a_{n} }}<1$ allora $\forall {\epsilon} \geq {0}, \exists {n_{0}} \text{ tale che } \forall {n} \geq {n_{0}}$, $l-\frac{\epsilon}{2}<\sqrt[n]{ a_{n} }<l+\frac{\epsilon}{2}$ e quindi $\sqrt[n]{ a_{n} }<(1-\epsilon)+\frac{\epsilon}{2}=1+\frac{\epsilon}{2}$  Allora $a_{n}<\left( 1-\frac{\epsilon}{2} \right)^n$ che converge e per il teorema del confronto anche $\{{a_{n}}\}_{n\in N}$ convergerà


---

### Criterio del rapporto

Sia $\{{a_{n}}\}_{n\in N}$ una successione positiva, se esiste il $\lim_{ n \to \infty } {\frac{{ a_{n+1} }}{a_{n}}}$ allora 
	• se $l<1$, $\sum_{i=0}^\infty{a_{i}}$ converge
	• se $l>1$, $\sum_{i=0}^\infty{a_{i}}$ diverge
	• se $l=1$ non si sa

### Dimostrazione

 $\forall {\epsilon} > {0}, \exists {N} | {n\geq N} \implies |\frac{a_{n+1}}{a_{n}}-l|<\epsilon$ quindi ho che $l-\epsilon<\frac{a_{n+1}}{a_{n}}<l+\epsilon$
 Se $\epsilon<l$ allora $(l-\epsilon)a_{n}<a_{n+1}<(l+\epsilon)a_{n}$
 1) Se $l<1$ scegliendo $\epsilon$ tale che $l+\epsilon<1$ si ha $$a_{n+1}<(l+\epsilon)a_{n}<(l+\epsilon)^{2}a_{n-1}<\dots<(l+\epsilon)^{n+1}a_{0}$$ e essendo $(l+\epsilon)^{n+1}$ una serie geometrica $<1$ converge per il teorema del confronto
 2) Se $l>1$ scegliendo $\epsilon$ tale che $l+\epsilon>1$ si ha $$a_{n+1}<(l+\epsilon)a_{n}<(l+\epsilon)^{2}a_{n-1}<\dots<(l+\epsilon)^{n+1}a_{0}$$  e essendo $(l+\epsilon)^{n+1}$ una serie geometrica $>1$ diverge per il teorema del confronto
 