## Integrale definito

```math
||{"id":1392903461886}||


```

Vorrei approssimare l'area della regione di piano sottesa da $f\in[a,b]$
Il rettangolo $x_{3}-x_{2}$ e altezza $f(z)$ ha area$f(z)(x_{3}-x_{2})$

Sia $f:[a,b]\to R$ una funzione, e sia $\{x_{0},x_{1},x_{2},x_{3},\dots\}$ una qualunque suddivisione dell'intervallo $[a,b]$, cioè $x_{0}=a,x_{n}=b,\forall {0\leq i\leq n} \text{ si ha } {x_{i}<x_{i+1}}$ e sia $z_{i}\in[x_{i},x_{i+1}]$ un punto qualunque, allora posso approssimare l'area sottesa al grafico di $f\in[x_{i},x_{i+1}]$ con quella del rettangolo di area $f(z_{i})(x_{i+1}-x_{i})$ e se le sommo tutte ho
$$
S_{n}(f)=\sum_{i=0}^{n-1}f(z_{i})(x_{i+1}-x_{i})
$$
e tale sommatoria prende il nome di somma di Cauchy-Rienman

Sia $f:[a,b]\to R$, se esiste ed è finito il limite delle somme di Cauchy-Rienman di $f\in[a,b]$ e non dipende dalla scelta degli $z_{i}$ allora $f$ si dice integrabile in $[a,b]$ e si pone
$$
\lim_{ n \to \infty } {S_{n}(f)} = \int_{a}^b f(x) \, dx 
$$
e si chiama integrale definito di $f(x)$ sull'intervallo di integrazione $[a,b]$

## Teorema

1. Sia $f:[a,b]\to R$ una funzione continua, allora $f$ è integrabile in $[a,b]$
2. Sia $f:[a,b]\to R$ una funzione monotona e limitata, allora $f$ è integrabile in $[a,b]$

>[!info]
>Se $f:[a,b]\to R$ è positiva in tutto $[a,b]$ allora $\int_{a}^{b}  f(x)\, dx$ allora rappresenta realmente l'area della regione sottostante $f$
>
>Se cambia segno allora $\int_{a}^{b}  f(x)\, dx$ sarà l'area sopra all'asse $x$ meno quella sotto

Sia $f:[a,b]\to R$, se $F:[a,b]\to R$ è tale che $F'(x)=f(x)$, si dice che $F(x)$ è una primitiva di $f(x_{})$

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

![[Integrali notevoli]]

## Regola della catena
$$
\int f'(g(x))g'(x) \, dx = f(g(x)) +c 
$$

## Integrazione per parti
$$
\int f'(x)g(x) \, dx = f(x)g(x) - \int f(x)g'(x) \, dx 
$$
Metodo per la scelta della $g(x)$
Metodo LInATE (priorità) -> log, inverse, algebriche, trig, exp

## Integrazione per sostituzione

Sia $f:[a,b]\to R$ continua e sia $\phi:[\alpha,\beta]\to[a,b]$ una funzione invertibile e derivabile con derivata continua, allora 
$$
\int_{a}^{b} f(x) \, dx = \int_{\alpha}^{\beta} f(\phi(t))\phi' \, dt 
$$
[[Formule trigonometriche]]

## Proprietà

1. $\int_{a}^{b} f(x_{}) \, dx=\int_{a}^{c} f(x_{}) \, dx+\int_{c}^{b} f(x_{}) \, dx$
2. $\int_{a}^{b} f(x_{}) \, dx=\int_{b}^{a} f(x_{}) \, dx$
3. $|\int_{a}^{b} f(x) \, dx|\leq \int_{a}^{b} |f(x)| \, dx$
4. ![[Disuguaglianza di Schwartz]]

### Monotonia

Siano $f,g:[a,b]\to R$ tale che $\forall {a\leq x\leq b} \text{ tale che } f(x_{})\leq g(x)$ allora $\int_{a}^{b} f(x_{}) \, dx \leq \int_{a}^{b} g(x) \, dx$

## Teorema del valor medio integrale

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

## Secondo teorema del calcolo integrale (Torricelli-Borrow)

Sia $f:[a,b]\to R$ una funzione continua in $[a,b]$ e sia  $x_{0}\in[a,b]$, sia poi 
$$
F(x)=\int_{x_{0}}^{x} f(t)  \, dt
$$
Allora $F(x)$ è detta funzione integrale di $f(x)$ e $F(x)$ è una funzione continua e derivabile in $[a,b]$ e $\forall {x} \in {[a,b]}$ si ha $F'(x)=f(x)$

>[!note]- Dimostrazione
>$F(x)=\frac{F(x+h)-F(x)}{h}=\frac{1}{h}\left( \int_{x}^{x+h} f(t)  \, dt-\int_{x+h}^{x} f(t)  \, dt \right)=\frac{1}{h}\int_{x}^{x+h} f(t)\, dt$
>Per il teorema del valor medio integrale $\frac{F(x+h)-F(x)}{h}=f(z)$ con $z\in[x,x+h]$
>Passando al limite per $h\to_{0}$ dove $z\to x$ dunque
>$$F'(x)=\lim_{ h \to 0 } {\frac{F(x+h)-F(x)}{h}}=\lim_{ z \to x } {f(z)}=f(x)$$
>

