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

## Teorema dell continuità delle derivate

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

## Lemma di Fermat

Sia $f:[a,b]\to R$ derivabile in $(a,b)$ se $x$ è un punto di minimo o di massimo allora 
$$
f'(x)=0
$$
>[!note]- Dimostrazione
> Sia $x_{0}$ punto di massimo locale cioè  esiste un $\delta>0$ per cui $M$ è massimo di $f$ in $[x_{0}-\delta,x_{0}+\delta]$ allora si dice che M è un massimo locale
> Calcolo $f'x_{0}$
$$f'(x_{0})= \lim_{ h \to 0 } \frac{f(x_{0}+h)-f(x_{0})}{h}$$
> per $h$ sufficientemente piccolo, si avrà $x_{0}+h\in(x_{0}-\delta,x_{0}+\delta)$
> 
> Perciò $f(x_{0}+h)-f(x_{0})\leq 0$ allora
>  $\lim_{ h \to 0^+ } \frac{f(x_{0}+h)-f(x_{0})}{h}\leq 0$ e $\lim_{ h \to 0^- } \frac{f(x_{0}+h)-f(x_{0})}{h}\geq 0$
>  
> Ma $f$ è derivabile in $x_{0}$ quindi $\lim_{ h \to 0 } \frac{f(x_{0}+h)-f(x_{0})}{h}$ deve esistere e questo deve essere $0$

