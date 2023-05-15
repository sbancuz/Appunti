---
tags: [analisi_2]
---
Una EDO del primo ordine si dice a variabili separabili se è della forma
$$
y'(t) = h(t) g(y(t)) , t \in I
$$
con $h: I_{1}\subseteq \mathbb R\to \mathbb R$ e $g: I_{2}\subseteq \mathbb R\to \mathbb R$ funzioni continue di variabili reali cioè in forma normale è 
$$
f(t,s) = h(t)g(s)
$$

>[!note] Esempio
>$$
>y'(t) = ty^{3} \implies h(t) =t \land g(s) = s^{3}
>$$

## Risoluzione

### Passo 1
Cerco le soluzioni costanti, quindi $g(s) = 0$

### Passo 2
Cerco le soluzioni non costanti.

#### Passo 2.1
Divido quindi l'EDO con $g(y(t))$, 
$$
\frac{y'(t)}{g(y(t))} = t
$$

#### Passo 2.2
Integro nell'intervallo $(t_{0},t)\in I$
$$
\int _{t_{0}}^{t}\frac{y'(r)}{g(y(r))} \, dr = \int _{t_{0}}^{t} r \, dr 
$$

#### Passo 2.3
Cambio variabili $z = y(r)$ e uso il teorema fondamentale del calcolo integrale
$$
\int _{y(t_{0})}^{y(t)} \, \frac{dz}{g(z)} = [F(z)]_{y(t_{0})}^{y(t)} = \int _{t_{0}}^{t} r \, dr = [F(r)]_{t_{0}}^{t}
$$

#### Passo 2.4
Trovare la forma esplicita per $y(t)$
$$
y(t) = h(t, c)
$$
con $h$ una qualsiasi funzione ottenuta dal passaggio.

### Passo 3
Scrivo l'integrale generale
$$
y(t) = h(t, c),  \forall {t } \in   {I} , y = 0, \forall {t} \in {J} 
$$

>[!info]
>I domini delle soluzioni sono diversi e devono essere strettamente inclusi nell'intervallo di definizione della EDO

>[!info]
>I grafici delle soluzioni non si intersecano mai e riempiono il dominio di $f$

