Sia $\{{a_{n}}\}_{n\in N}$ una successione, si può definire una seconda successione $\{{s_{n}}\}_{n\in N}$ in questo modo:$$
\begin{align}
s_{0} & =a_{0}\\
s_{1} & =a_{0}+a_{1}\\
s_{2} & =a_{0}+a_{1}+a_{2} \\
 & \dots\\
s_{n} & =a_{0}+a_{1}+\dots+a_{n} = \sum_{i=0}^na_{i} = s_{n-1}+a_{n}\\
\end{align}
$$La successione $\{{s_{n}}\}_{n\in N}$ si chiama successione delle somme parziali di $\{{a_{n}}\}_{n\in N}$
Poiché $\{{s_{n}}\}_{n\in N}$ è una successione posso calcolare il limite per n->$\infty$
$$
\lim_{ n \to \infty } {\sum_{i=0}^nai} = \sum_{i=0}^\infty{a_{i}}

$$
La scrittura $\sum_{i=0}^\infty{a_{i}}$ si chiama SERIE a termini $a_{i}$
Poiché una serie è un limite di una successione, una serie può essere regolare o irregolare.

Se la serie $\sum_{i=0}^\infty{a_{i}}$ è regolare e convergente, allora converge alla sua somma $s$

## Serie geometrica

$$
\sum_{i=0}^\infty{q^i}=\lim_{ n \to \infty } \frac{{1-q^{n+1}}}{1-q}=
\left\{\begin{align}
+\infty & &   q \geq 1 \\
\frac{1}{1-q} & &  -1<q<q \\
irregolare &  & q \lt -1\\
\end{align}
\right|
$$

## Studio del carattere

Poiché una serie è un limite il carattere di una serie può essere:
	• regolare convergente
	• regolare divergente
	• irregolare

