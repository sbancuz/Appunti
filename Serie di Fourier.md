---
tags: analisi_2
---
### [[Polinomio trigonometrico]]

### Coefficienti di Fourier

Data $f: \mathbb{R}\to \mathbb{R}$ $2\pi$-periodica definiamo coefficienti di Fourier relativi a $f$ i seguenti:
$$
\begin{align}
a_{0}  & = \frac{1}{2\pi}\int _{-\pi}^{\pi}f(x) \, dx \\
a_{n}  & = \frac{1}{\pi} \int _{-\pi}^{\pi}f(x)\cos(nx) \, dx  \\
b_{n}  & = \frac{1}{\pi} \int _{-\pi}^{\pi}f(x)\sin(nx) \, dx   
\end{align}
$$

### Teorema per il calcolo dei coefficienti di Fourier

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


### Serie di Fourier

Data una funzione $f: \mathbb{R} \to \mathbb{R}$ $2\pi$-periodica chiamiamo polinomio di Fourier di ordine $m\in \mathbb{N}_{0}$ associato a $f$ il seguente:
$$
F_{m}(x) =a_{0}+\sum^{m}_{n=1}(a_{n}\cos(nx)+b_{n}\sin(nx))
$$
con $a_{0}, a_{n}, b_{n}$ definiti come coefficienti di Fourier, mentre chiamiamo serie di Fourier di $f$ il limite (se esiste)
$$
\lim_{ m \to \infty } {F_{m}(x)}
$$

### Convergenza => [[Polinomio trigonometrico]]

### Convergenza puntuale

Sia $f: \mathbb{R}\to \mathbb{R}$ $2\pi$-periodica e regolare a tratti in $[-\pi,\pi]$ allora la serie di Fourier $f$ converge puntualmente in tutto $\mathbb{R}$

>[!warning]
>Non è detto che converga necessariamente a $f$ in tutti i punti

In particolare, sia $F_{m}(x)$ il polinomio di Fourier di ordine $m\in \mathbb{N}$ associato a $f$, si ha che:
1) se $f$ è continua in $x$ allora $\lim_{ m \to \infty } {F_{m}(x)} = f(x)$
2) se $f$ è discontinua in $x$ allora $\lim_{ m\to \infty } {F_{m}(x)} = \frac{1}{2} (\lim_{ s \to x^{+} }f(s) + \lim_{ s \to x^{-} } {f(s)})$ 

### Convergenza totale della serie di Fourier e integrabilità

Sia $f:\mathbb{R}\to \mathbb{R}$ $2\pi$-periodica e regolare a tratti in $[-\pi,\pi]$, se $f$ è continua in $\mathbb{R}$ allora la serie di Fourier di $f$ converge totalmente a $f$ in tutto $\mathbb{R}$ e vale la formula di integrabilità termine a termine negli intervalli limitati.

### Derivabilità termine a termine

Sia $f:\mathbb{R}\to \mathbb{R}$ $2\pi$-periodica e tale che:
1) $f$ è derivabile su $\mathbb{R}$, e quindi regolare a tratti
2) $f'$ è regolare a tratti in $[-\pi,\pi]$
3) $f'$ è continua

Allora la serie è derivabile in $\mathbb{R}$

### Convergenza in media quadratica

Sia $f:\mathbb{R}\to \mathbb{R}$ $2\pi$-periodica, si dice che la serie di Fourier converge in norma quadratica a $f$ se 
$$
\lim_{ m \to \infty } {\int _{-\pi}^{\pi}|f(x)-F_{m}(x)|^{2} \, dx  = 0}
$$

### Teorema

Sia $f:\mathbb{R}\to \mathbb{R}$ $2\pi$-periodica e regolare a tratti in $[-\pi,\pi]$. Allora la serie di Fourier di $f$ converge in norma quadratica a $f$.

### Diseguaglianza di Bessel

Sia $f:\mathbb{R}\to \mathbb{R}$ $2\pi$-periodica e regolare a tratti in $[-\pi,\pi]$.  Siano $a_{0},a_{n}, b_{n}\in\mathbb{R}$ i coefficienti di Fourier di $f$. Abbiamo che 
$$
2a_{0}^{2} + \sum(a_{n}^{2} + b_{n}^{2})\leq \frac{1}{\pi}\int _{-\pi}^{\pi}|f(x)|^{2} \, dx 
$$

### Identità di Parseval

Sia $f:\mathbb{R}\to \mathbb{R}$ $2\pi$-periodica e regolare a tratti in $[-\pi,\pi]$.  Siano $a_{0},a_{n}, b_{n}\in\mathbb{R}$ i coefficienti di Fourier di $f$. Abbiamo che 
$$
2a_{0}^{2} + \sum(a_{n}^{2} + b_{n}^{2})= \frac{1}{\pi}\int _{-\pi}^{\pi}|f(x)|^{2} \, dx 
$$

### Forma esponenziale

Dalla formula di Eulero $e^{ix}=\cos x+i\sin x$ e $e^{i(-x)} = \cos x-i\sin x$ quindi
$$
\cos x = \frac{{e^{ix} + e^{-ix}}}{2} \text{ e }\sin x = \frac{{e^{ix}-e^{-ix}}}{2i}
$$
e sostituendo $x$ con $nx$ riesco ad ottenere
$$
F_{m}(x) = \sum_{-\infty}^{\infty}c_{n}e^{inx}, c_{n} = \left( \frac{a_{n}}{2} - \frac{ib_{n}}{2} \right)
$$