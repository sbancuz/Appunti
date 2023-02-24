---
tags: [analisi 1]
---
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