---
tags: [analisi 1]
---
## Primo teorema fondamentale del calcolo integrale

Sia $f:[a,b]\to R$ una funzione continua, allora se $F$ è una primitiva di $f$ allora 
$$
\int_{a}^{b} f(x) \, dx =F(b)-F(a)
$$

>[!note]- Dimostrazione
>$F(b)-F(a)=F(x_{n})-F(x_{0})=F(x_{n})-F(x_{n-1})+F(x_{n-1})-F(x_{n-2})+\dots$
>
>Allora $\sum_{i=0}^{x-1}(F(x_{i+1})-F(x_{i}))$ è continua e deribabile in $[a,b]$ e per il teorema di Lagrange si ha che $$\frac{F(x_{i+1})-F(x_{i})}{x_{i+1}-x_{i}}=F'(z_{i})=f(z_{i})$$
>
>Cioè $F(x_{i+1})-F(x_{i})=f(z_{i})(x_{i+1}-x_{i})$
>
>Allora $F(b)-F(a)=\sum_{i=0}^{n-1}f(z_{i})(x_{i+1}-x_{i})$ che è la somma di C-R, passando al limite $$F(b)-F(a)=\lim_{ n \to \infty } \sum_{i=0}^{n-1}f(z_{i})(x_{i+1}-x_{i})=\int_{a}^{b} f(x_{}) \, dx $$

>[!tip]
>Una funzione ha molte primitive infatti $$\int f(x) \, dx = F(x) + c$$
>
>Se non è definita su un intervallo, ma su unione di più intervalli allora questo non è più vero, ma tra i sottointervalli allora vale
