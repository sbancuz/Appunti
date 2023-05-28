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