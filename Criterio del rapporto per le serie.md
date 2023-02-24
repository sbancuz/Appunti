---
tags: [analisi 1]
---

Sia $\{{a_{n}}\}_{n\in N}$ una successione positiva, se esiste il $\lim_{ n \to \infty } {\frac{{ a_{n+1} }}{a_{n}}}$ allora 
	• se $l<1$, $\sum_{i=0}^\infty{a_{i}}$ converge
	• se $l>1$, $\sum_{i=0}^\infty{a_{i}}$ diverge
	• se $l=1$ non si sa

> [!note]- Dimostrazione
> $\forall {\epsilon} > {0}, \exists {N} | {n\geq N} \implies |\frac{a_{n+1}}{a_{n}}-l|<\epsilon$ quindi ho che $l-\epsilon<\frac{a_{n+1}}{a_{n}}<l+\epsilon$
> Se $\epsilon<l$ allora $(l-\epsilon)a_{n}<a_{n+1}<(l+\epsilon)a_{n}$
> 1. Se $l<1$ scegliendo $\epsilon$ tale che $l+\epsilon<1$ si ha $$a_{n+1}<(l+\epsilon)a_{n}<(l+\epsilon)^{2}a_{n-1}<\dots<(l+\epsilon)^{n+1}a_{0}$$ e essendo $(l+\epsilon)^{n+1}$ una serie geometrica $<1$ converge per il teorema del confronto
> 2. Se $l>1$ scegliendo $\epsilon$ tale che $l+\epsilon>1$ si ha $$a_{n+1}<(l+\epsilon)a_{n}<(l+\epsilon)^{2}a_{n-1}<\dots<(l+\epsilon)^{n+1}a_{0}$$ e essendo $(l+\epsilon)^{n+1}$ una serie geometrica $>1$ diverge per il teorema del confronto