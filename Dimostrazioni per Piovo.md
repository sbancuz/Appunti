---
tags: analisi_2
---
### Struttura dell'integrale generale delle EDO del secondo ordine lineare

Siano $a,b,c:I\subset \mathbb R\to \mathbb R$ continue con $a\neq 0$.

L'integrale generale dell'equazione omogenea è
$$
a(t)y''(t)+b(t)y'(t)+c(t)y(t)=0
$$
ed è uno [[Spazio vettoriale]] di dimensione 2, cioè le soluzioni sono tutte della forma
$$
y_{\sigma}(t) = c_{1}y_{\sigma,1}(t)+c_{2}y_{\sigma,2}(t)
$$
con $c_{1},c_{2}\in \mathbb R$, dove $y_{\sigma,1}$ e$y_{\sigma,2}$ sono le 2 soluzioni linearmente indipendenti

#### Dimostrazione

Dal principio di sovrapposizione deduciamo che l'insieme di tutte le soluzioni è uno spazio vettoriale.

Per dimostrare che la dimensione è 2 dobbiamo:

1) determinare 2 soluzioni linearmente indipendenti $y_{\sigma,1},y_{\sigma,2}$
Fissiamo $t_{0}\in I$ e scegliamo  $y_{\sigma,1}$ e $y_{\sigma,2}$ come soluzioni di 2 problemi di Cauchy, rispettivamente  $y_{\sigma,1}$ soluzione di
$$
\begin{cases}
a(t)y''(t)+b(t)y'(t)+c(t)y(t)=f(t) \\
y(t_{0}) = 1 \\
y'(t_{0}) = 0
\end{cases}
$$
e $y_{\sigma,2}$ soluzione di
$$
\begin{cases}
a(t)y''(t)+b(t)y'(t)+c(t)y(t)=f(t) \\
y(t_{0}) = 0 \\
y'(t_{0}) = 1
\end{cases}
$$
Tali soluzioni esistono uniche grazie al teorema di esistenza e unicità globale per il problema di Cauchy. Manca solo da verificare l'indipendenza lineare.

Per assurdo prendo $\exists {c} \neq {0}$  tale che $y_{\sigma ,{1}}(t) = cy_{\sigma,2}(t), \forall {t} \in {I}$. Allora per definizione di $y_{\sigma,1}$ e $y_{\sigma,2}$ abbiamo che 
$$
1=y_{\sigma,1}(t_{0}) = cy_{\sigma,2}(t_{0}) = c \times0 = 0
$$
che è una contraddizione.

2) verificare che ogni soluzione particolare si può scrivere come combinazione lineare di  $y_{\sigma,1}$ e $y_{\sigma,2}$
Sia $\overline{y}_{\sigma}$ una qualunque soluzione particolare della EDO, allora cerco $c_{1},c_{2}\in \mathbb R$ per cui $\overline{y}_{\sigma}$ coincide con la funzione 
$$
z(t)=c_{1}y_{\sigma,1}+c_{2}y_{\sigma,2}
$$
Scegliamo $c_{1}$ e $c_{2}$ in maniera tale che $\overline{y}_{\sigma} = z(t_{0})$ e $y'_{\sigma}(t_{0}) = z'(t_{0})$ ovvero
$$
\begin{cases}
\overline{y}_{\sigma}(t_{0}) = z(t_{0}) = c_{1}y_{\sigma,1}(t_{0})+c_{2}y_{\sigma,2}(t_{0}) = c_{1} \\
\overline{y}_{\sigma}'(t_{0}) = z'(t_{0}) = c_{1}y'_{\sigma,1}(t_{0})+c_{2}y'_{\sigma,2}(t_{0}) = c_{2} 
\end{cases}
$$
Per questa scelta di costanti la funzione diventa $y_{\sigma}(t) = y_{\sigma,1}(t)+y_{\sigma,2}(t)$. Concludiamo osservando che sia $z(t)$ che $\overline{y}_{\sigma}(t)$ soddisfano il problema di Cauchy
$$

\begin{cases}
a(t)y''(t)+b(t)y'(t)+c(t)y(t)=f(t) \\
y(t_{0}) = \overline{y}_{\sigma}(t_{0}) \\
y'(t_{0}) = \overline{y}'_{\sigma}(t_{0}) 
\end{cases}
$$
e quindi per il teorema di esistenza e unicità globale del problema di Cauchy abbiamo che $\overline{y}_{\sigma}(t)=z(t), \forall {t} \in {I}$ e questo conclude la dimostrazione.

---

### Calcolo raggio di convergenza

Data la serie di potenze $\sum_{n=0}^\infty{a_{n}(x-x_{0})^{n}}$ abbiamo che, se uno dei seguenti limiti esiste:
$$
\begin{align}
R=\lim_{ n \to \infty } {|\frac{a_{n}}{a_{n+1}}|} \\
R =\lim_{ n \to \infty } {\frac{1}{\sqrt[n]{  |a_{n}|}}}
\end{align}
$$
allora la serie ha raggio di convergenza $R$

>[!warning]
>I criteri del rapporto e della radice per le serie numeriche sono legati a $\frac{1}{R}$

#### Dimostrazione

Grazie al teorema del raggio di convergenza è sufficiente verificare che la serie 
$$
\sum_{n=0}^\infty{|a_{n}(x-x_{0})^{n}|}
$$
converge per $|x-x_{0}|<R$ e che non converge per $|x-x_{0}|>R$

1) Osserviamo che tutte le serie di potenza convergono per $x=x_{0}$ e che per $x\neq x_{0}$ abbiamo
$$
\lim_{ n \to \infty } \frac{{|a_{n+1}(x-x_{0})^{n+1}|}}{|a_{n}(x-x_{0})^{n}|} = |x-x_{0}|\lim_{ n \to \infty } \frac{{|a_{n+1}|}}{a_{n}} = \frac{{|x-x_{0}|}}{R}
$$
e quindi le ipotesi sono dirette conseguenza del criterio del rapporto per la serie numerica

2) Osserviamo che $\forall {x} \in {\mathbb R}$
 $$
\lim_{ n \to \infty } {\sqrt[n]{|a_{n}(x-x_{0})^{n}|  }} = |x-x_{0}|\lim_{ n \to \infty } {\sqrt[n]{ a_{n} }} = \frac{|x-x_{0}|}{R}
$$
e quindi le ipotesi sono dirette conseguenze del criterio della radice per la serie numerica

---

Teorema per il calcolo dei coefficienti di Fourier

Se $f: \mathbb{R}\to \mathbb{R}$ $2\pi$-periodica è somma di una serie trigonometrica con convergenza totale su $[-\pi,\pi]$ allora abbiamo che $a_{0},a_{n},b_{n}$ sono i coefficienti di Fourier di $f$

>[!tip]
>Se $f$ è pari su $(-\pi,\pi)$ => $b_{n} = 0$
>
>Se $f$ è dispari su $(-\pi,\pi)$ => $a_{n} = 0$

#### Dimostrazione

Assumiamo che $\exists {a_{0},a_{n},b_{n}} \in   {}\mathbb{R}$ tali che 
$$
f(x)=a_{0}+\sum(a_{n}\cos(nx)+b_{n}\sin(nx))
$$
con convergenza totale su $[-\pi,\pi]$

Iniziamo con $a_{0}$ e calcoliamo:
$$
\begin{align}
\int _{-\pi}^{\pi}f(x) \, dx  & = \int _{-\pi}^{\pi}a_{0}+\sum(a_{n}\cos(nx)+b_{n}\sin(nx)) \, dx \\
 & = \int _{-\pi}^{\pi}a_{0} \, dx +\sum a_{n}\int _{-\pi}^{\pi}\cos(nx) \, dx +\sum b_{n}\int _{-\pi}^{\pi}\sin(nx) \, dx  \\
  & = a_{0}2\pi + 0 +0 =a_{0}2\pi
\end{align}
$$
Proseguiamo con $a_{k}$:
$$
\begin{align}
\int _{-\pi}^{\pi}f(x)\cos(kx) \, dx  & = \int _{-\pi}^{\pi}\left( a_{0}+\sum(a_{n}\cos(nx)+b_{n}\sin(nx))  \right)\ \cos(kx), dx \\
 & = \int _{-\pi}^{\pi}a_{0}\cos(kx) \, dx +\sum a_{n}\int _{-\pi}^{\pi}\cos(nx)\cos(kx) \, dx +\sum b_{n}\int _{-\pi}^{\pi}\sin(nx)\cos(kx) \, dx  \\
  & = 0 + \pi a_{k} +0 =\pi a_{k}
\end{align}
$$
Ed infine $b_{k}$
$$
\begin{align}
\int _{-\pi}^{\pi}f(x)\sin(kx) \, dx  & = \int _{-\pi}^{\pi}\left( a_{0}+\sum(a_{n}\cos(nx)+b_{n}\sin(nx))  \right)\ \sin(kx), dx \\
 & = \int _{-\pi}^{\pi}a_{0}\sin(kx) \, dx +\sum a_{n}\int _{-\pi}^{\pi}\cos(nx)\sin(kx) \, dx +\sum b_{n}\int _{-\pi}^{\pi}\sin(nx)\sin(kx) \, dx  \\
  & = 0 + 0 + b_{k}\pi =\pi b_{k}
\end{align}
$$

---

### Teorema di invarianza della lunghezza di una curva per riparametrizzazioni

Sia $\underline{r}:[a,b] \subseteq \mathbb R \to \mathbb R^n$ una curva regolare di sostegno $\gamma$ e sia $\underline{v}: [c,d] \subseteq \mathbb R \to \mathbb R^n$ una riparametrizzazione di $\gamma$ relativa al cambiamento di variabile $\phi:[c,d] \to [a,b]$. Abbiamo che 
$$
L(\underline{r}([a,b])) = \int _{c}^{d} | | v'(s)| |  \, ds = \int _{a} ^{b} | | \underline{r}'(t)| |  \, dt 
$$

#### Dimostrazione

Ricordiamo che siccome $\underline{r}$ è regolare, abbiamo che $L(\underline{r}([a,b])) =\int _{a} ^{b} | | \underline{r}'(t)| |  \, dt$.
Unendo la formula di derivazione di funzione composte componente per componente otteniamo $\forall {s} \in {(c,d)}$
$$
\underline{v}'(s) = (\underline{r}(\phi(s)))' = \underline{r}'(\phi(s))\phi'(s)
$$
e quindi,
$$
|| \underline{v}'(s) | | = | \phi'(s) | \cdot | | \underline{r}'(\phi(s))| |
$$
Vogliamo fare il cambio di variabile $t=\phi(s)$ che implica $dt = \phi'(s)ds$ e per gli estremi di integrazione abbiamo due possibilità:
- Se $\phi$ è crescente allora $\phi(c) = a<b=\phi(d), \phi'(s)\geq 0$ $\forall {s} \in {(c,d)}$ e $|| \underline{v}'(s) | | =  \phi'(s)  \cdot | | \underline{r}'(\phi(s))| |$
- Se $\phi$ è decrescente allora $\phi(c) = b<a=\phi(d), \phi'(s)\leq 0$ $\forall {s} \in {(c,d)}$ e $|| \underline{v}'(s) | | =  -\phi'(s)  \cdot | | \underline{r}'(\phi(s))| |$

Nel primo caso abbiamo che
$$
\int _{a}^{b} | | \underline{r}'(t) | | dt \, = \int _{c} ^d  \underline{r}'(\phi(s))\phi'(s)\, ds  = \int _{c} ^d  || \underline{v}'(s)| | \, ds   
$$
Nel secondo caso
$$
\int _{a}^{b} | | \underline{r}'(t) | | dt \, = \int _{d} ^c  \underline{r}'(\phi(s))(-\phi'(s))\, ds  = \int _{c} ^d  \underline{r}'(\phi(s))\phi'(s)\, ds = \int _{c} ^d  || \underline{v}'(s)| | \, ds   
$$

---

### Teorema della matrice Hessiana

Siano $A\subseteq \mathbb R^n$ aperto, $f\in\mathcal C^{2}(A)$ e $\underline{x}_{0}\in A$ critico di $f$. Sia $q:\mathbb R^n\to \mathbb{R}$ la forma indotta dalla matrice Hessiana $H_{f}(\underline{x}_{0})$. Abbiamo che
1) Se q è definita positiva, allora $\underline{x}_{0}$ è punto di minimo
2) Se q è definita negativa, allora $\underline{x}_{0}$ è punto di massimo
3) Se q è indefinita, allora $\underline{x}_{0}$ è di sella

>[!note]
>In caso la funzione sia semi-definita il teorema non ci dice nulla

#### Dimostrazione

La matrice Hessiana $H_{f}(\underline{x}_{0})$ è:
1) simmetrica per Schwarz
2) ha tutti gli autovalori reali e positivi siccome la forma quadratica indotta da $H_{f}$ è definita positiva

Da 1) deduciamo che 
$$
q(\underline{h}) = \left< \underline{h},H_{f}(\underline{x}_{0} )\underline{h} \right> \geq \lambda_{min}||\underline{h}||^{2}
$$
dove $\lambda_{min}$ denota l'autovalore più piccolo. Dato che $\underline{x}_{0}$ è un punto critico, dalla formula di Taylor al secondo ordine otteniamo che
$$
f(\underline{x}_{0}+\underline{h}) - f(\underline{x}_{0}) = \cancel{\left< \triangledown f(\underline{x}_{0}), \underline{h} \right> } + \frac{1}{2}q(\underline{h}) + \sigma(||\underline{x}||^{2}) \geq \frac{1}{2} \lambda_{min}||\underline{h}||^{2} + \sigma(||\underline{h}||^{2})
$$
per $||\underline{h}||\to0$.

Per la definizione di $\sigma$-piccolo abbiamo che 
$$
\lim_{ \underline{h} \to 0 } \frac{{\sigma(||\underline{h}||^{2})}}{||\underline{h}||^{2}} = 0
$$
e quindi $\exists {\delta} > {0}$ tale che, se $||\underline{h}||<\delta$ e $\underline{h}\neq 0$ allora
$$
 \frac{|{\sigma(||\underline{h}||^{2})|}}{||\underline{h}||^{2} } < \frac{1}{4}\lambda_{min}
$$
e siccome da 2) $\lambda_{min}>0$  si può concludere che
$$
\begin{align}
f(\underline{x}_{0}+\underline{h}) - f(\underline{x}_{0})  & \geq \frac{1}{2} \lambda_{min}||\underline{h}||^{2} + \sigma(||\underline{h}||^{2}) \\
  & \geq \frac{1}{2} \lambda_{min}||\underline{h}||^{2} - \frac{1}{4} \lambda_{min}||\underline{h}||^{2} \\
   &  = \frac{1}{4}\lambda_{min}||\underline{h}||^{2} \geq 0
\end{align}
$$
$\forall {\underline{h}} \in {B_{\delta}(0)}$ tale che $\underline{x}_{0}+\underline{h}\in A$, che implica che, $\underline{x}_{0}$ è un punto minimo locale di $f$

---

### Coordinate sferiche

La funzione relativa alle coordinate sferiche è
$$
\underline{T}_{s}: \mathbb{R}^{+}\times[0,\pi]\times[0,2\pi) \to \mathbb{R}^{3}
$$
$$
\left( \begin{matrix}
\rho\\\phi\\\theta
\end{matrix} \right) 
 \to \left( \begin{matrix}
\rho \sin\phi \cos\theta \\
\rho \sin\phi \sin\theta \\
\rho \cos\phi
\end{matrix} \right) =
\left( \begin{matrix}
x\\y\\z
\end{matrix} \right) 
$$
$$
\iiint _{\Omega}f(x,y,z) \ dxdydz = \iiint _{T_{\rho}^{-1}(\Omega)} f(\rho \sin\phi\cos\theta,\rho \sin\phi\sin\Theta,\rho \cos\theta)\rho^{2}\sin\phi\ d\rho d\theta dz
$$

### Dimostrazione

Abbiamo che 
$$
J_{\underline{T}s}(\rho,\phi,\theta) = \left( \begin{matrix}
\sin\phi \cos\theta  & \rho \cos\phi \cos\theta  & -\rho \sin\phi \cos\theta \\
\sin\phi \sin\theta & \rho \cos\phi \sin\theta & \rho \sin\phi \cos\theta \\
\cos\phi & -\rho \sin\phi & o
\end{matrix} \right) 
$$
e quindi il determinante sarà $\rho^{2}\sin\phi$

---

Condizione necessaria per la differenziabilità

Sia $A\subseteq \mathbb R^n$ aperto, $f_:A\to \mathbb{R}$ differenziabile.  Allora $f$ è continua in $\underline{x}_{0}$

#### Dimostrazione

Dobbiamo dimostrare che $\exists {\lim_{ \underline{x} \to \underline{x}_{0} }} f(\underline{x}) = f(\underline{x}_{0}) {}$

Siccome $f$ è differenziabile in $\underline{x}_{0}$, abbiamo che
$$
f(\underline{x}) = f(\underline{x}_{0}) + <\underline{a}, \underline{x} - \underline{x}_{0}> + \sigma(||\underline{x}-\underline{x}_{0}||)
$$
e quindi grazie alla diseguaglianza triangolare e a quella di Cauchy-Schwarz 
$$
0\leq |f(\underline{x})-f(\underline{x}_{0})| \leq ||\triangledown f(\underline{x}_{0})|| \cdot ||\underline{x}-\underline{x}_{0}||+ \sigma(||\underline{x}-\underline{x}_{0}||)
$$
Prendendo il limite per $\underline{x}\to \underline{x}_{0}$ si ottiene
$$
0\leq \lim_{ \underline{x} \to \underline{x}_{0} } {}|f(\underline{x})-f(\underline{x}_{0})| \leq\lim_{ \underline{x} \to \underline{x}_{0} } ||\triangledown f(\underline{x}_{0})|| \cdot ||\underline{x}-\underline{x}_{0}||+ \lim_{ \underline{x} \to \underline{x}_{0} }\sigma(||\underline{x}-\underline{x}_{0}||) = 0+0 = 0
$$
e quindi concludiamo che 
$$
\lim_{ \underline{x} \to \underline{x}_{0} } {}|f(\underline{x})-f(\underline{x}_{0})| = 0
$$
---

### Formula del gradiente

Sia $A\subseteq \mathbb R^n$ aperto, $f_:A\to \mathbb{R}$ differenziabile.  Allora per ogni [[Versori]] $\underline{v}\in \mathbb R^n$ esiste la derivata direzionale in $\underline{x}_{0}$ lungo la direzione $\underline{v}$ e inoltre
$$
\frac{ \partial f }{ \partial \underline{v} } = <\triangledown f(\underline{x}_{0}), \underline{v}>
$$

#### Dimostrazione

Siccome $f$ è differenziabile in $\underline{x}_{0}$, abbiamo che 
$$
f(\underline{x}_{0} + \underline{h}) = f(\underline{x}_{0}) + <\triangledown f(\underline{x}_{0}),\underline{h}> + \sigma(||\underline{h}||)
$$
per $\underline{h}\to0$ e applichiamo tale equazione a $\underline{h}=t\underline{v}$ per $t\in\mathbb{R}$ piccolo ottenendo 
$$
f(\underline{x}_{0} + t\underline{v}) = f(\underline{x}_{0}) + <\triangledown f(\underline{x}_{0}),t\underline{v}> + \sigma(t)
$$
e quindi
$$
\begin{align}
\frac{{f(\underline{x}_{0} + t\underline{v}) - f(\underline{x}_{0})}}{t}  & =  \frac{{<\triangledown f(\underline{x}_{0}),t\underline{v}>}}{t} + \frac{{\sigma(t)}}{t} \\
  & = {<\triangledown f(\underline{x}_{0}),\underline{v}>} + \frac{{\sigma(t)}}{t}
\end{align}
$$
e concludiamo che 
$$
\frac{ \partial f }{ \partial \underline{v} } = \lim_{ t \to 0 } {\frac{{f(\underline{x}_{0} + t\underline{v}) - f(\underline{x}_{0})}}{t} } = \lim_{ t \to 0 } {<\triangledown f(\underline{x}_{0}), \underline{v}>} + \lim_{ t \to 0 } \frac{{\sigma(t)}}{t} = <\triangledown f(\underline{x}_{0}), \underline{v}>
$$

---

### Ortogonalità del gradiente agli insiemi di livello

Sia $A\subseteq \mathbb R^n$ aperto e $f:A\to \mathbb{R}$ differenziabile. Supponiamo che l'insieme di livello $k\in\mathbb{R}$ di $f$, cioè
$$
I_{k}  =\{ \underline{x}\in A:f(\underline{x}) = k \}
$$
sia il sostegno di una curva regolare $\underline{r}: I\to A$ dove $I \subseteq \mathbb{R}$ è un intervallo. Abbiamo allora che
$$
\left<  \triangledown f(\underline{r}(t)), \underline{r}'(t) \right> = 0 
$$

#### Dimostrazione

Abbiamo che 
$$
\{ \underline{r}(t) : t\in I \} = I_{k} = \{ \underline{x} \in \mathbb R^n : f(\underline{x}) = k \}
$$
e quindi $f(\underline{r}(t)) = k$ e $F(t) = f(\underline{r}(t))) = k, \forall {t} \in {I}$ ovvero $F$ è costante su I e quindi
$$
F'(t) = 0
$$
per il teorema di derivazione delle funzioni composte abbiamo che 
$$
F'(t) = \left< \triangledown f(\underline{r}(t)), \underline{r}'(t) \right> 
$$
Quindi otteniamo che 
$$
F'(t) = \left<  \triangledown f(\underline{r}(t)), \underline{r}' \right> = 0, \forall {t} \in {I}  
$$
---

### Teorema) Formula risolutiva per le EDO del primo ordine lineari

Date $a,b$ continue su $I$, l'integrale generale della EDO è dato dalla formula
$$
y(t) = e^{A(t)}[B(t) + c], t \in I
$$
dove $c\in \mathbb R$, $A$ è la primitiva di $\int  a\,$, e $B$ è una qualunque primitiva di $\int b \, e^{-A}$

#### Dimostrazione

Svolgiamo 3 passi:
- Passo 1) Porto a sinistra il termine con la $a$ e moltiplico per $e^{-A}$ => $(ye^{-A})' = y'e^{-A}-aye^{-A} = be^{-A}$
- Passo 2) Applico il (TFCI) troviamo la primitiva su entrambi i membri
$$
ye^{-A} = \int(ye^{-A})'  \, dt = \int  be^{-A} \, dt + c 
$$
 - Passo 3) Moltiplico per $e^{A}$ e ottengo 
 $$
y(t) =e ^{A(t)}\left[ \int be^{-A(t)} \, dt +c  \right]
$$
