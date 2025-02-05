---
tags: [analisi_1]
---
Per calcolare la radice quadrata di un numero negativo basta avere la $\sqrt{-1} = i$ infatti $$\text{se} \lt 0\to\sqrt{a} = \sqrt{i*|a|}$$
Aggiungo a $R$ quindi $i^2 = -1$ in modo tale da poter esprimere tutte le espressioni come $$x+iy \text{ con } x,y \in R$$
Un numero complesso $z = x+iy$ dove $x,y \in R$ e $i^2=-1$, l'[[insieme]] di tutte queste espressioni si indica con $C$ il [[Campo]] non ordinato dei numeri complessi. 
I numeri $C$ hanno le stesse proprietà di $R$ e possono essere rappresentati come punti nel piano $C\to R^2$
```math
||{"id":274371783654}||

z =2+3i
```

Si indica con $\Re(z)=x$ la parte reale di z e con $\Im(z)=y$ la sua parte immaginaria 

## Operazioni
• somma -> $z+z_1 = (x+x_1)+i(y+y_1)$
• prodotto -> $zz_1 = (xx_1-yy_1)+i(xx_1+yy_1)$
• differenza ->$z-z_1 = (x-x_1)+i(y-y_1)$
• divisione -> se $z_1\not=0$ allora $\frac{z}{z_1}=\frac{xx_1+yy_1}{x_1^2+y_1^2}+i\frac{xx_1-yy_1}{x_1^2+y_1^2}$
• coniugato -> $\overline{z}=x-iy$
• modulo -> $|z| = \sqrt{x^2+y^2}$ e rappresenta la distanza da $(0,0)$

### Proprietà modulo e coniugato
• se $z\in C$ | $z\ge0$ e $|z| =0$ sse $z=0$
• se $z\in C$ | $|z| = |\overline{z}| = |-z|$ 
• se $z,w\in C$ $\begin{align}\overline{z+w} &= \overline{z}+\overline{w} \\\overline{z*w} &= \overline{z}*\overline{w} \\\overline{(\frac{z}{w})} &= \frac{\overline{z}}{\overline{w}} \\\end{align}$
• se $z\in C$ | $z*\overline{z}=|z|^2$ 
• se $z,w\in C$ | $|z+w| \le |z|+|w|,|z+w| \ge ||z|-|w||$ 


## Forma trigonometrica

Purché $\not=(0,0)$ un punto complesso può essere descritto con la coppia $(\rho,\theta)$
```math
||{"id":77617332589}||

z = \rho(cos(\theta)+isen(\theta))
\rho = sqrt{x^2+y^2}
\theta = atan(\frac{b}{a})
```

L'$Arg(z)$ non è unico, è periodico per $2k\pi$ 

>[!info]
>Sommare e sottrarre con la rappresentazione normale non è un problema, ma per moltiplicare e dividere diventa laborioso

Siano $z = \rho(cos(\theta)+isen(\theta))$ e $z_1 = \rho_1(cos(\theta_1)+isen(\theta_1))$ allora $$\begin{align}
z*z_1 &= \rho*\rho_1(cos(\theta+\theta_1) + isen(\theta+\theta_1)) \\
z/z_1 &= \rho/\rho_1(cos(\theta-\theta_1) + isen(\theta-\theta_1))\end{align}
$$
![[Teorema di De Moivre]]

### Interpretazione geometrica
```math
||{"id":997833838030}||
|z*i| = |z|*|i| =|z|
Arg(z*i) = Arg(z) + Arg(i) = Arg(z) + {\pi }/2
```
![[Teorema fondamentale dell'algebra]]

## Radici n-esime 

Dalla formula di de-Moivre per la potenza n-esima, si trova quella per il calcolo delle radici n-esime

Sia $w\in C$ e $n\in N$, si dice che $z\in C$ è una radice n-esima di $w$ se $z^n=w$
Se $w\not=0$ e $n\in N$ esistono esattamente n diverse radici di $w = \rho(cos(\theta)+isen(\theta))$
$$
\forall0\le k\le n-1 \rightarrow
\left\{
\begin{align}
\rho_k&=\sqrt[n]{\rho} \\
\theta_k &= \frac{\theta + 2k\pi}{n}
\end{align}
\right|
$$
```math
||{"id":1310643447814}||

\sqrt[6](1+i)
```
