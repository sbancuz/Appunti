```math
||{"id":511109335375}||




```
La pendenza della retta che passa per $(x_{0},f(x_{0}))$ e $(x_{0})+h,f(x_{0}+h)$ è $$
\frac{f(x_{0}+h)-f(x_{0})}{h}
$$
che è chiamato il rapporto incrementale di $f(x)$ in $x_{0}$. 
Se esiste ed è finito il limite di $h\to_{0}$ esso rappresenterà la pendenza della retta tangente al grafico di $f$ in $(x_{0},f(x_{0}))$

Si definisce derivata $$
\lim_{ h \to 0 } \frac{f(x_{0}+h)-f(x_{0})}{h} = \lim_{ x \to x_{0} } \frac{f(x)-f(x_{0})}{x-x_{0}}
$$
Sia $f:(a,b)\to R$ e sia $x_{0}\in(a,b)$ si dice che $f$ è derivabile in $x_{0}$ se esiste ed è finito il   $$
\lim_{ h \to 0 } \frac{f(x_{0}+h)-f(x_{0})}{h}
$$
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
