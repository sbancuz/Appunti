---
tags: [analisi_1]
---

### Teorema di convergenza delle successioni monotone limitate in $\mathrm{R}$

Sia $x_{n}\in R$ una successione di numeri reali monotona crescente quindi
$$
\forall {n} \geq {0} \implies x_{n}\leq x_{n+1} 
$$
e superiormente limitata che vuol dire
$$
\exists {M} \in {R} \text{ tc } x_{m}\leq M \text{  } \forall {m} \geq  {0}   
$$

Allora $\{x_{n}\} \subset R$ è di Cauchy e quindi convergente cioè
$$
\exists {\lim_{ n \to \infty } {x_{n}}} \in {R} 
$$

### Dimostrazione

Per la completezza di $R$ è sufficiente mostrare che la successione $x_{n}$ sia di Cauchy. Cioè
$$
\forall {\epsilon} > {0}, \exists {N(\epsilon)} \geq {0} \text{ | }  n,m \geq N(\epsilon) \implies |x_{n}-x_{m}| < \epsilon
$$
Per assurdo supponiamo che la successione $\{X_{m}\}$ non abbia questa proprietà. Quindi 
$$
\exists {\epsilon} > {0} \text{ | } \forall {N} \geq {1}, \exists {m_{N},n_{N}} \geq  {N} \text{ tc } |x_{m_{N}}-x_{n_{N}}| \geq \epsilon   
$$

Possiamo assumere che il punto $x_{m_{N}}\geq x_{n_{N}}$ così $x_{m_{N}}\geq \epsilon+x_{n_{N}}$ 
Per $N_{1}=1, \exists {m_{1}>n_{1}} \text{ tc } x_{m_{1}} \geq \epsilon x_{n_{1}}$
Per $N_{2}=m_{1}, \exists {m_{2}>n_{2}\geq N_{2} = n_{1}>m_{1}}$

Allora avremo che $x_{n_{2}}\geq 2\epsilon +x_{m_{1}}$ e più in generale
$$
X_{K+1}=m_{k}>m_{k}, \exists {m_{k+1}>n_{k+1}} >N_{k+1}>m_{k}>n_{k}>\dots>k\epsilon+x_{n_{1}} 
$$
Per la monotonia del limite non esiste
$$
\lim_{ n \to \infty } {x_{m_{k+1}}} \geq \lim_{ k \to \infty } {k\epsilon+x_{n_{1}}} = \infty
$$
e quindi $\{x_{n}\}$ è di Cauchy.

____

### Esistenza di SUP e INF in R

Se $A\subseteq R$ è superiormente limitato, cioè ha almeno un maggiorante, allora $\exists {\sup A} \subseteq {R}$

### Dimostrazione

Poiché $A$ è superiormente limitato possiamo dire che $\exists {b_{0}} \in {R} \text{ tc } x\in A \implies x \leq b_{0}$  

Sia ora $a_{0}\in A$ fissato, avremo che $[a_{0},b_{0}]\cap A\neq 0$.
Consideriamo il punto medio $c = \frac{a_{0}+b_{0}}{2}$ e consideriamo $[a_{0},c],[c,b_{0}]$ in cui in almeno una delle 2 metà vi saranno punti di $A$.

Consideriamo tra le due metà quella più a destra che contiene punti di $A$ con $[a_{1},b_{1}]$ e $b_{1}$ è maggiorante di $A$. 

Ripeto il procedimento per dicotomia.

Quello che ottengo è una successione decrescente di intervalli tale che $b_{n}$ è maggiorante di $A$.

${a_{n}}$ è crescrente e superiormente limitata da $b_{0}$ invece ${b_{n}}$ è decrescrente e inferiormente limitata da $a_{0}$.

Allora per il teorema di convergenza delle successioni monotonelimitate 
$$
\exists {\lim_{ n \to \infty } {a_{n}}} ,\exists {\lim_{ n \to \infty } {b_{n}}} , \exists {\lim_{ n \to \infty } {(b_{n}-a_{n})}} =\lim_{ n \to \infty } {\frac{b_{0}-a_{0}}{2^{n}}} = \overline{x} \in R
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

Sia $E \subseteq R$ limitato e infinito, allora $\exists {}  {}$ almeno un punto di accumulazione quindi $E'\neq 0$.

### Dimostrazione

Visto che $E$ è limitato, quindi è contenuto in un intervallo $E\subseteq[a_{0},b_{0}]$. Sia $c=\frac{a_{0}+b_{0}}{2}$il punto medio e consideriamo adesso $[a_{0},c], [c,b_{0}]$ in cui in almeno una delle 2 vi sono infiniti punti.
Scelgo una delle 2 metà che contiene infiniti punti di $E$ e la chiamo $[a_{1},b_{1}]$. 

Facendo per dicotomia otteniamo una successione descrescente di intervalli 
$$
[a_{n+1},b_{n+1}]\subset[a_{n},b_{n}]\subset\dots[a_{0},b_{0}]
$$
tali che ogni intervallo abbia cardinalità infinita.

${a_{n}}$ è crescrente e superiormente limitata da $a_{0}$ invece ${b_{n}}$ è decrescrente e inferiormente limitata da $b_{0}$
$$
\lim_{ n \to \infty } {(b_{n}-a_{n})= \lim_{ n \to \infty } {\frac{b_{0}-a_{0}}{2^{n}}}=0}\implies \exists {\lim_{ n \to \infty } {a_{n}}} , \exists {\lim_{ n \to \infty } {b_{n}}} = \overline{x}  
$$

Scegliamo $x_{n}\in E\cap[a_{n},b_{n}]$ con $x_{n}\neq \overline{x}$, e possiamo farlo poiché in quell'intervallo vi sono infiniti punti di $E$. Quindi
$$
\lim_{ n \to \infty } {a_{n}}\leq \lim_{ n \to \infty } {x_{n}}\leq \lim_{ n \to \infty } {b_{n}} \implies \overline{x} = \lim_{ n \to \infty } {x_{n}}
$$
$\overline{x}$ sarà sicuramente punto di accumulazione.

____
