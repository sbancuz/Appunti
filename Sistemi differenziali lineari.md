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

### Definizione

Un SDL di ordine n è un sistema di n EDO lineari del primo ordine
$$
\underline{y}'(x) = A(x)\underline{y}(x)+\underline{b}(x)
$$
nella funzione incognita $\underline{y}:J\subseteq \mathbb R^{n}$ con 
$$
\underline{y}(x) = 
\left(
\begin{matrix}
y_{1}(x) \\
\vdots \\
y_{n}(x)
\end{matrix}
\right),
A=\left(
\begin{matrix}
a_{11}(x) & \dots & a_{1n}(x) \\
\vdots  & \ddots  & \vdots\\
a_{n1}(x) & \dots  & a_{nn}(x)
\end{matrix}
\right), \underline{b}= 
\left(
\begin{matrix}
b_{1}(x) \\
\vdots \\
b_{n}(x)
\end{matrix}
\right)
$$
Se $\underline{b} = 0$ allora il sistema lineare è detto omogeneo se no completo

### Passare da [[EDO del secondo ordine lineare]] a sistema 

Una generica EDO del secondo ordine lineare a coefficiente costante è della forma
$$
ay''(x)+by'(x)+cy(x)=f
$$
con $a,b,c,f\in\mathbb R$ e $a\neq 0$ 

Sia quindi $y_{1}(x)=y(x)$e $y_{2}(x)=y'(x)$ ottenendo
$$
\begin{cases}
y_{1}'(t)=y_{2}(t) \\
y_{2}'(t)= -\frac{b}{a}y_{2}(x)-\frac{c}{a}y_{1}(x)+\frac{f}{a}
\end{cases}
$$
o con le [[Matrici]]
$$
\underline{y}'(x) = A\underline{y}(x) + \underline{b}
$$
con
$$
\underline{y}(x) = 
\left(
\begin{matrix}
y_{1}(x) \\
y_{2}(x)
\end{matrix}
\right),
A=\left(
\begin{matrix}
0 & 1 \\
-\frac{c}{a} & -\frac{b}{a}
\end{matrix}
\right), \underline{b}= 
\left(
\begin{matrix}
0 \\
\frac{f}{a}
\end{matrix}
\right)
$$
>[!note]
> In realtà si può trasformare una qualunque EDO lineare di ordine n come sistema di n EDO lineari del primo ordine

### [[Problema di Cauchy]]

### Teorema di esistenza e unicità globale per il problema di Cauchy associato a SDL

Se $A:I\subseteq \mathbb R \to M_{n\times n}$ e $\underline{b}:I\to \mathbb R^{n}$ sono funzioni continue, allora il problema di Cauchy ammette un unica soluzione definita su tutto $I$. Inoltre se il sistema è omogeneo l'unica soluzione costante è la soluzione $\underline{y}(x)=0 \in I$

### Teorema [[Principio di sovrapposizione]]

### [[Sistemi lineari omogenei]]
### [[Sistemi lineari non omogeneo]]