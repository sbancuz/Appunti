---
tags: [analisi_2]
---
Introduciamo i sistemi differenziali lineari descrivendo la relazione con le EDO del secondo ordine lineari.

1) Oscillazioni meccaniche: ottenuta dalla legge fondamentale della dinamica
$$
my''(t)=-hy'(t)-ky'(y)+f(t) 
$$
2) Circuiti elettrici RLC
3) Pendolo con oscillazioni

Se consideriamo la 1) con $h=k=0$ allora si ottiene
$$
y''(t)= g \implies y(t) =\frac{1}{2}g(t)^{2}+c_{1}t+c_{2}
$$

Considero la risoluzione con i sistemi e quindi riscrivo l'equazione come un sistema di 2 EDO del primo ordine
$$
y_{1}(t)=y(t), y_{2}(t) = y'(t)
$$
Si osserva quindi che $y_{1}'(t) = y'(t)=y_{2}(t)$ e $y_{2}'(t)=y''(t)=g$
Quindi il sistema sarà
$$
\begin{cases}
y_{1}'(t)=y_{2}(t) & \text{<= EDO 1 ordine}\\
y_{2}'(t)=g & \text{<= EDO 1 ordine}
\end{cases}
$$
In questo caso possiamo risolverlo con la teoria delle [[Equazioni differenziali ordinarie|equazioni del primo ordine]]
