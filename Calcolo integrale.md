---
tags: [analisi_1]
---
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
![[Primo teorema fondamentale del calcolo integrale]]

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
4. Se $\int_{a}^{b} f({x}) \, dx$ ha $f(x)$ pari $\implies 2\int_{0}^{b} f(x) \, dx$
5. 4. Se $\int_{a}^{b} f({x}) \, dx$ ha $f(x)$ dispari $\implies 0$
6. ![[Disuguaglianza di Schwartz]]

### Monotonia

Siano $f,g:[a,b]\to R$ tale che $\forall {a\leq x\leq b} \text{ tale che } f(x_{})\leq g(x)$ allora $\int_{a}^{b} f(x_{}) \, dx \leq \int_{a}^{b} g(x) \, dx$

![[Teorema del valor medio integrale]]

![[Secondo teorema del calcolo integrale (Torricelli-Borrow)]]

## Teorema

Sia $f$ continua e $F$ una sua funzione integrale, se $f$ cambia segno in un [[intorno]] di un punto $x_{0}$, allora in $x$ $F$ ha un minimo oppure un massimo

## Integrali con Taylor

Sia $f:[a,b]\to R$ derivabile n volte e sia $F$ una sua funzione integrale, allora $F$ è derivabile $n+1$ volte e quindi è sviluppabile in polinomio di Taylor
$$
F(x)=\sum_{k=0}^{n+1} \frac{f^{(k)}(x_{0})}{k!}\frac{(x-x_{0})^k}{k+1} + o(x^{n+1})
$$



[[Serie di Taylor]]

## Integrali impropri o generalizzati

Sia $f:[a,b)\to R$ tale che per $x\to b^{-}$ si abbia $f(x)\to \infty$ si dice che $f$ è integrabile in senso improprio in $b$ se esiste finito
$$
\lim_{ t \to b^{-} } {\int_{a}^{t}  f(x)\, dx }
$$
In tale caso, tale limite finito è l'integrale improprio di $f(x)$ in $[a,b)$. Analogamente se $f$ è illimitata per $x->a^{+}$

>[!warning]
>Se $f$ è illimitata sia in $a$ che in $b$ allora sarà integrabile in senso improprio in $(a,b)$ sse $\forall {c} \in (a,b) {}$ solo se risulta integrabile in $(a,c],[c,b)$


## Teorema

Sia $\alpha\in R$ allora gli integrali impropri
$$
\int_{a}^{b} \frac{1}{(b-x)^{\alpha}} \, dx \text{ e } \int_{a}^{b} \frac{1}{(x-a)^{\alpha}} \, dx  
$$
sono convergenti sse $\alpha<1$ e divergenti se $\alpha\geq 1$

>[!tip]
>Una regione illimitata del piano può avere area finita

![[Teorema del confronto integrale]]

![[Teorema del confronto asintotico integrale]]

## Teorema 

Sia $f:[a,b]\to R$ continua tale che $\lim_{ x \to b^{-} } {f(x)}=\infty$, si dice che $f$ è assolutamente integrabile in b se è integrabile in b la funzione $|f(x)|$ cioè esiste finito
$$
F(x)=\int_{a}^{b} |f(x)| \, dx 
$$

## Integrazione su intervalli illimitati

Sia $f:[a,\infty)\to R$ continua si dice che $f$ è integrabile in senso improprio in $[a,\infty)$ se esiste finito
$$
\lim_{ t \to \infty } {\int_{a}^{t}  f(x)\, dx }
$$

### Teorema

Sia $\alpha>0$ allora
$$
\int_{1}^{\infty} \frac{1}{x^{\alpha}} \, dx \implies
\left\{
\begin{align}
 & \text{converge sse } \alpha>1 \\
 & \text{diverge sse } 0<\alpha\leq1 \\
\end{align}
\right|
$$

## Teorema del confronto

Siano $f,g:[a,\infty)\to R$ continue in $[a,\infty)$ e tali che $\lim_{ x \to \infty } {f(x)}=\lim_{ x \to \infty } {g(x)}=+\infty$ e inoltre $\forall {x} \in {[a,\infty)}$ si abbia $0\leq f(x)\leq g(x)$, si ha
1. se $g$ è integrabile in $\infty$, lo è anche $f$
2. se $f$ non è integrabile in $\infty$, lo è anche $g$

## Corollario 

Affinché $\int_{a}^{\infty} g(x) \, dx$ converga, deve essre $\lim_{ x \to \infty } {g(x)}$ = 0, cioè $g(x)$ è infinitesima per $x\to \infty$

## Teorema del confronto asintotico

Siano $f,g:[a,\infty)\to R$ continue in $[a,\infty)$ e $\forall {x} \in {[a,\infty)}$ sia $f(x)g(x)> 0$ e $\lim_{ x \to \infty } {f(x)}=\lim_{ x \to \infty o } {g(x)}=\infty$

Se per $x\to \infty$ si ha $f(x)\sim g(x)$ allora $f(x)$ è integrabile in $\infty$ sse lo è anche $g(x)$
Se $f(x)=o(g(x))$ per $x\to \infty$ e $g$ è integrabile a $\infty$, allora anche $f$ lo è
Se $f$ è assolutamente integrabile a $\infty$ allora $f$ è integrabile a $\infty$

### ==> [[Calcolo integrale per funzioni a più variabili]]
