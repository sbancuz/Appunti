---
tags: [analisi_1]
---
```math
||{"id":511109335375}||




```

La pendenza della retta che passa per $(x_{0},f(x_{0}))$ e $(x_{0})+h,f(x_{0}+h)$ è $$\frac{f(x_{0}+h)-f(x_{0})}{h}$$
che è chiamato il rapporto incrementale di $f(x)$ in $x_{0}$. 
Se esiste ed è finito il limite di $h\to_{0}$ esso rappresenterà la pendenza della retta tangente al grafico di $f$ in $(x_{0},f(x_{0}))$

Si definisce derivata $$\lim_{ h \to 0 } \frac{f(x_{0}+h)-f(x_{0})}{h} = \lim_{ x \to x_{0} } \frac{f(x)-f(x_{0})}{x-x_{0}}$$
Sia $f:(a,b)\to R$ e sia $x_{0}\in(a,b)$ si dice che $f$ è derivabile in $x_{0}$ se esiste ed è finito il   $$\lim_{ h \to 0 } \frac{f(x_{0}+h)-f(x_{0})}{h}$$
e si pone tale limite uguale a $f'(x_{0})$ e si chiama derivata di $f$ in $x_{0}$

Se poi si ha che $\forall {x} \in {(a,b)}$ $f$ è derivabile in $x$, si dice che $f$ è derivabile nell'intervallo $(a,b)$
In tal caso resta definita una funzione da $(a,b)\in R$ che associa ad ogni $x\in(a,b)$ la derivata di $f$ in $x$, tale funzione si chiama funzione derivata di $f$ e si indica con $f'$

Per costruzione, se $f$ è derivabile in $x_{0}$ allora la retta tangente al grafico di $f$ in $(x_{0},f(x_{0}))$ ha equazione $$
y=f'(x_{0})(x-x_{0})+f(x_{0})
$$

>[!info]
>La $f'$ è una funzione normale, e quindi posso definire la sua funzione derivata con $f''$ e così via

![[Derivate fondamentali]]

## Teorema della continuità delle derivate

Sia $f$ derivabile in $x_{0}$, allora $f$ è continua in $x_{0}$

>[!note]- Dimostrazione
>Sia $\lim_{ h \to 0 } \frac{f(x_{0}+h)-f(x_{0})}{h}=f'(x_{0})\in R$ allora per $h\to {0}$ ho che ${f(x_{0}+h)-f(x_{0})}\sim f'(x_{0})h$ perciò $\lim_{ h \to 0 } {f(x_{0}+h)}=\lim_{ h \to 0 } {(f(x_{0})+f'(x_{0})h)}=f(x_{0})$ quindi f è continua in $x_{0}$

## Algebra delle derivate

La derivate è una funzione lineare

Siano $f,g$ due funzioni derivabili allora
	1. $(fg)'=f'g+fg'$
	2. $\left( \frac{f}{g} \right)'=\frac{f'g-fg'}{g^2}$
	3. $(g(f))'=f'g'(f)$

## Derivata dell'inversa di una funzione

Sia $f:(a,b)\to R$ derivabile e inveribile e sia $g$ la sua inversa. Sia $x_{0}\in(a,b)$ tale che $f'(x_{0})\neq 0$ e sia $y_{0}=f(x_{0})$, allora $g$ è derivabile in $y_{0}$ e vale $$g'(y_{0})=\frac{1}{f'(x_{0})}$$
>[!note]- Dimostrazione
>$y_{0}=f(x_{0})$, quidni $g(y_{0})=x_{0}$; inoltre poniamo $f(x_{0}+h)-f(x_{0}) = k$ quindi $f(x_{0}+h)=y_{0}+k$.
>Ora calcolo $g'(y_{0})$ con la definizione:
>$$
>\lim_{ k \to 0 } \frac{g(y_{0}+k)-g(y_{0})}{k}=\lim_{ k \to 0 } {\frac{h}{k}}=\lim_{ h \to 0 } {\frac{h}{f(x_{0}+h)-f(x_{0})}}=\frac{1}{f'(x_{0})}
>$$


## Punti di non derivabilità

Una prima possibilità è che non esista il limite del rapporto incrementale, ma esistono finiti e diversi i limiti per $h\to{0}^+$ e per $h\to{0}^-$ e in questo caso si dice che $f$ ha un punto angoloso
```math
||{"id":1474030729501}||
f(x)=|x|

```

Sia $f:(a,b)\to R$ e $x_{}\in (a,b)$, se esiste finito $\lim_{ h \to 0^+ } \frac{f(x_{0}+h)-f(x_{0})}{h}$ si dice che $f$ è derivabile a destra in $x_{0}$ e si indica con $f'_{+}(x_{0})$, stessa cosa per sinistra

Un'altro motivo di non derivabilità è quando il limite del rapporto incrementale è $\infty$

Sia $f$ continua in $x_{0}$ e $\lim_{ h \to 0 } \frac{f(x_{0}+h)-f(x_{0})}{h}$, allora la retta tangente al grafico di $f$ in $(x_{0},f(x_{0}))$ esiste ma è verticale ed è detto flesso o una cuspide(2 flessi opposti vicini)
```math
||{"id":996311213761}||


```
## Ricerca di massimi e minimi di una funzione

Sia $f:[a,b]\to R$, si dice che $M\in R$ è il massimo di $f\in [a,b]$ se $\forall {x} \in {[a,b]}$ si ha $f(x)\leq M$;  $m\in R$ è il minimo di $f\in [a,b]$ se $\forall {x} \in {[a,b]}$ si ha $f(x)\geq m$

Se $M\in R$ è tale che esiste un $\delta>0$ per cui $M$ è massimo di $f$ in $[x_{0}-\delta,x_{0}+\delta]$ allora si dice che M è un massimo locale
Se $m\in R$ è tale che esiste un $\delta>0$ per cui $m$ è minimo di $f$ in $[x_{0}-\delta,x_{0}+\delta]$ allora si dice che m è un minimo locale

![[Lemma di Fermat]]

![[Teorema di Lagrange]]

## Test di monotonia

Sia $f:(a,b)\to R$ derivabile in $(a,b)$, allora:
	1. $f$ è crescente in $(a,b)$ sse $\forall {x} \in {(a,b)}$ si ha $f'(x)\geq 0$
	2. $f$ è decrescente in $(a,b)$ sse $\forall {x} \in {(a,b)}$ si ha $f'(x)\leq 0$

>[!note]- Dimostrazione
>Siano $x_{1},x_{2}\in(a,b)$ allora se:
>
>$f$ è crescente in $(a,b)$ sse $\forall {x_{1},x_{2}} \in {(a,b)}$ con $x_{1}\neq x_{2}$ si ha $\frac{f(x_{1})-f(x_{2})}{x_{1}-x_{2}}\geq 0$
>
>$f$ è decrescente in $(a,b)$ sse $\forall {x_{1},x_{2}} \in {(a,b)}$ con $x_{1}\neq x_{2}$ si ha $\frac{f(x_{1})-f(x_{2})}{x_{1}-x_{2}}\leq 0$
>
>Passando al limite per $x_{2}\to x_{1}$ 
>1. se $f$ è crescente -> $f'(x_{1})\geq0$ 
>2. se $f$ è decrescente -> $f'(x_{1})\leq0$ 
>
>Per provare che $f$ è crescente, applico Lagrange ad $f$ in $[x_{1},x_{2}]$, quindi $x_{2}-x_{1}>0$, $f'(c)\geq 0$ per ipotesi, allora $f(x_{2})-f(x_{1})\geq 0$ e quindi la $f$ è crescente 

### Corollario

Sia $f:(a,b)\to R$, allora $\forall {x} \in {(a,b)}$ tale che $f'(x)=0$ sse $f$ è costante in $(a,b)$

## Estensione di una funzione

Sia $f:[a,c)\cup(c,b]\to R$, se esistono finiti $\lim_{ x \to c^- } {f(x)}$ e $\lim_{ x \to c^+ } {f(x)}$ allora posso definire 
$$
g(x) = \left\{\begin{align}
	f(x), &  & \text{se }x\neq c \\
	\lim_{ x \to c } {f(c)} &  & \text{se }x=c
\end{align}
\right|
$$
e $g(x)$ estende la continuità di $f$ in $c$

>[!tip]
>La stessa cosa si può fare con $f'$ e in questo caso sarebbe un estensione in derivabilità

![[Teorema di de L'Hospital]]

## Limite della derivata e derivabilità

Se $f:[a,b]\to R$ è continua in $[a,b]$ e derivabile in $[a,c)\cup(c,b]$ con $c\in[a,b]$
Per stabilire se $f$ è derivabile in $c$ dovrei fare il limite del rapporto incrementale. Ma se f' risulta continua o prolungabile con continuità in $c$, posso concludere che $f$ è derivabile in $c$?

Sia $f:[a,b]\to R$ continua in $[a,b]$ e derivabile in $(a,b)$, se esiste
$$
\lim_{ x \to a^+ } {l }\in R\cup\{-\infty,\infty\} 
$$
allora $f'_{+}(a)$ esiste ed è uguale a $l$
Stesso vale in $b$

>[!note]- Dimostrazione
>Sia $h>0$, posso applicare Lagrange a $f$ in $[a,a+h]$ allora $\exists {t_{h}}\in  {(a,a+h)}$ tale che
>$$
>f'(t_{h})=\frac{f(a+h)-f(a)}{h}\to_{h\to 0^+}l
>$$

## Derivata seconda

Un sottoinsieme A di $R^2$ si dice convesso se $\forall {P,P'} \in A {}$ il segmento congiungente $P$ e $P'$ è tutto contenuto in $A$ 
```math
||{"id":437174172797}||


```
Sia $f:[a,b]\to R$, si chiama sopragrafico e epigrafico di $f$ l'[[insieme]]
$$
epi(f)=\{(x,y)\in R^2 \text{ tale che } x \in[a,b],y\geq f(x)\}
$$

Si dice che $f$ è convessa in $[a,b]$ se $epi(f)$ è convesso
Si dice che $f$ è concava in $[a,b]$ se $epi(-f)$ è convesso  

Sia $f:(a,b)\to R$ se:
	1. $f$ è convessa in $(a,b)$ sse $f'$ è crescente in $(a,b)$, è concava in $(a,b)$ sse $f'$ è decrescente in $(a,b)$
	2. $f$ è derivabile 2 volte allora è convessa in $(a,b)$ sse $f''(x)\geq 0$ in $(a,b)$; concava sse $f''(x)\leq 0$ in $(a,b)$  

ANALISI 2 -> [[Equazioni differenziali ordinarie]]