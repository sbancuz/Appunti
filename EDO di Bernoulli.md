---
tags: [analisi_2]
---

Si chiamano equazioni di Bernoulli le EDO del primo ordine non lineari del tipo
$$
y'(t) = g(t)y(t)+h(t)y^{\alpha}(t)
$$
dove $g,h: I\subseteq\mathbb R\to \mathbb R$ continue su $I$, e $\alpha\in \mathbb R$  e $\alpha \neq 0\neq 1$ e $h$ non è costantemente nulla.

>[!info]
>Le equazioni di Bernoulli sono in forma normale

## Risoluzione

### Passo 1
Ricerca soluzioni costanti
$$
0=f(t,y) = g(t)y(t)+h(t)y^{\alpha}(t) \implies \dots
$$
 - se $\alpha>0, y= 0$ è soluzione
 - se $h,g$ sono costanti, allora posso formalmente trovare le soluzioni seguenti e poi controllare se sono definite
	- $\alpha\in(0,1)$ => le soluzioni sono $y=0, y = \left( -\frac{h}{g} \right)^{\frac{1}{1-\alpha}}$ 
	- $\alpha > 1$ => le soluzioni sono $y=0, y = \left( -\frac{g}{h} \right)^{\frac{1}{\alpha - 1}}$
	- $\alpha<0$ => le soluzioni sono $y = \left( -\frac{h}{g} \right)^{\frac{1}{1-\alpha}}$

### Passo 2
Ricerca soluzioni non costanti

#### Passo 2.1
Divido EDO per $y^{\alpha}$
$$
\frac{d}{dt} \left[ \frac{1}{1-\alpha} \frac{1}{(y(t))^{\alpha-1}} \right]=\frac{y'(t)}{y^{\alpha}(t)} = g(t)\frac{y(t)}{y^{\alpha}(t)} + h(t)
$$
#### Passo 2.2
Pongo $z(t) = y^{1-\alpha}(t)$ così  da ottenere e moltiplico per $1 - \alpha$
$$
\frac{1}{1-\alpha} z'(t) = g(t)z(t) + h(t) \implies 
 z'(t) = (1-\alpha)g(t)z(t) + (1-\alpha)h(t)
$$
che è lineare

#### Passo 2.3
Risolvo come se fosse una [[EDO Lineari]]

#### Passo 2.4
Ricavo $y(t) = (z(t))^{\frac{1}{1-\alpha}}$

### Passo 3
Scrivere integrale generale mettendo assieme soluzioni costanti e non costanti