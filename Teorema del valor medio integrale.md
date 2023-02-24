---
tags: [analisi 1]
---
Siano $[a,b]\in R$, con $a<b$ e sia $f:[a,b]\to R$ continua allora $\exists {z} \in {[a,b]}$ tale che 
$$
\int_{a}^{b} f(x) \, dx =(b-a)f(z)
$$
>[!note]- Dimostrazione
>Poiché $f$ è continua in $[a,b]$, per il teorema di Weiestrass $f$ ha minimo e massimo in $[a,b]$
>
>Per la monotonia dell'integrale abbiamo che:
>$$(b-a)m=\int_{a}^{b} m \, dx \leq \int_{a}^{b} f(x) \, dx \leq \int_{a}^{b} M \, dx = M(b-a)$$
>Per il teorema dei valori intermedi, $\exists {z} \in {[a,b]}$  tale che  $f(z)$ è un valore compreso tra m e M di $f$, quindi
>$$f(z)=\frac{\int_{a}^{b} f(x) \, dx}{(b-a)}$$