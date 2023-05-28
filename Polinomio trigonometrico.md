---
tags: analisi_2
---
### Polinomio trigonometrico

Denotiamo come polinomio trigonometrico di ordine $m\in \mathbb{N}$ la funzioni $P_{m}$ periodica di periodo $2\pi$ del tipo:
$$
P_{m} (x) = a_{0} + \sum(a_{n}\cos(nx)+b_{n}\sin(nx))
$$
per $a_{0},a_{n},b_{n}\in \mathbb{R}$ che vengono chiamati coefficienti del polinomio trigonometrico, definito $\forall {x} \in {\mathbb{R}}$

In particolare i polinomi trigonometrici con $a_{0}=0$ e tutti gli altri coefficienti nulli a parte uno sono dette armoniche n-esime

>[!note]
>Ogni armonica n-esima è periodica di periodo $\frac{2\pi}{n}$ e quindi $P_{m(x)}$ è periodico di periodo $2\pi$

>[!warning]
>In altri testi $a_{0}$ è preso come $\frac{a_{0}}{2}$

### Formule di ortogonalità delle armoniche n-esime
$$
\begin{align}
\int _{-\pi}^{\pi}\cos(nx)\cos(kx) \, dx  & = \begin{cases}
0 & n\neq k \\
\pi & n=k
\end{cases}  \\
\int _{-\pi}^{\pi}\sin(nx)\sin(kx) \, dx  & = \begin{cases}
0 & n\neq k \\
\pi & n=k
\end{cases}  \\
\int _{-\pi}^{\pi}\sin(nx)\cos(kx) \, dx  & = 0
\end{align}
$$

### Serie trigonometrica -> [[Serie notevoli]]

### Funzione periodica => [[Proprietà delle funzioni]]

>[!note]
>La periodicità non implica la regolarità, possiamo quindi anche includere le funzioni discontinue

### Convergenza a partire dai coefficienti

Data una serie trigonometrica generica, abbiamo che:
1) Se la serie numerica di termine generale $|a_{n}| + |b_{n}|$ è convergente allora la serie converge totalmente in $\mathbb{R}$, inoltre la somma sarà continua ed è possibile integrare termine a termine su intervalli limitati
2) Se la serie numerica di termine generale $n(|a_{n}| + |b_{n}|)$ è derivabile e la derivata è data dalla serie delle derivate termine a termine

### Funzione regolare a tratti => [[Funzioni ad 1 variabile continue]]