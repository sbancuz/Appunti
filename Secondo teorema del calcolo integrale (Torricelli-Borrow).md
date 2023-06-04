---
tags: [analisi_1]
---
Sia $f:[a,b]\to R$ una funzione continua in $[a,b]$ e sia  $x_{0}\in[a,b]$, sia poi 
$$
F(x)=\int_{x_{0}}^{x} f(t)  \, dt
$$
Allora $F(x)$ è detta funzione integrale di $f(x)$ e $F(x)$ è una funzione derivabile in $[a,b]$ e $\forall {x} \in {[a,b]}$ si ha $F'(x)=f(x)$

>[!note]- Dimostrazione
>$F(x)=\frac{F(x+h)-F(x)}{h}=\frac{1}{h}\left( \int_{x}^{x+h} f(t)  \, dt-\int_{x+h}^{x} f(t)  \, dt \right)=\frac{1}{h}\int_{x}^{x+h} f(t)\, dt$
>Per il teorema del valor medio integrale $\frac{F(x+h)-F(x)}{h}=f(z)$ con $z\in[x,x+h]$
>Passando al limite per $h\to_{0}$ dove $z\to x$ dunque
>$$F'(x)=\lim_{ h \to 0 } {\frac{F(x+h)-F(x)}{h}}=\lim_{ z \to x } {f(z)}=f(x)$$
>

In generale sia $f,g:[a,b]\to R$ continue e $g(x)$ derivabile
$$
F(x)=\int_{a}^{g(x)} f(t) \, dt\implies F'(x)=f(g(x))g'(x)
$$