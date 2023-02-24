---
tags: [analisi 1]
---
Sia $f:[a,b]\to R$, continua in $[a,b]$ e derivabile in $(a,b)$, allora
$$
\exists {c} \in {(a,b)} \text{ tale che } f'(c)=\frac{{f(b)-f(a)}}{b-a} 
$$
```math
||{"id":181311675580}||


```
Geometricamente, c è un punto tra a e b in cui la retta tangente al grafico di $f$ in $(c,f(c))$ risulta parallela alla congiungente dei punti $(a,f(a)),(b,f(b))$

>[!note]- Dimostrazione
>La retta per i punti $(a,f(a)),(b,f(b))$ ha equazione
>$$
>y=\frac{{f(b)-f(a)}}{b-a} (x-a)+f(a)
>$$
>Considero la funzione ausiliaria
>$$
>w(x)= f(x) - \left( \frac{{f(b)-f(a)}}{b-a} (x-a)+f(a) \right)
>$$
>Si ha che $w(a)=w(b)=0$, $w(x)$ è continua in $[a,b]$ e derivabile in $(a,b)$.
>Per il teorema di Weiestrass esistono punto di max e min per $w \in [a,b]$:
>1. se $w(x_{1})=w(x_{2})$ allora w è costante, quindi $\forall {x} \in {[a,b]}, w'(x)=0$, quindi $f'(x)=\frac{{f(b)-f(a)}}{b-a}$
>2. se $w(x_{1})\neq w(x_{2})$ allora uno dei due è diverso sia da $a$ che da $b$, allora supponiamo che $x_{1}\neq a$ che $x_{2}\neq b$, allora $x_{1}$ è estremante per $w \in (a,b)$ e per Fermat $w'(x)=0$, quindi $f'(x)=\frac{{f(b)-f(a)}}{b-a}$