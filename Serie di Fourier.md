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