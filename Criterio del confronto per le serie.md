---
tags: [analisi_1]
---

Siano $\{{a_{n}}\}_{n\in N}$ e $\{{b_{n}}\}_{n\in N}$ successioni tali che definitivamente siano non negative e sia $a_{n}\leq b_{n}$ allora:
	1. se $\sum_{i=0}^\infty{b_{n}}$ converge, allora $\sum_{i=0}^\infty{a_{n}}$ converge
	2. se $\sum_{i=0}^\infty{a_{n}}$ diverge, allora $\sum_{i=0}^\infty{b_{n}}$ diverge

>[!note]- Dimostrazione
>1. Sia $n_{0}$ tale che $\forall {n} \geq {n_{0}}$ si abbia $0\leq a_{n}\leq b_{n}$
>	e siano $s_{n_{1}}=\sum_{i=n_{0}}^\infty{a_{i}}$ e $s_{n_{2}}=\sum_{i=n_{0}}^\infty{b_{n}}$ con $n\geq n_{0}$,
>	allora $\forall {n} \geq {n_{0}}$ si ha che $s_{n_{1}}\leq s_{n_{2}}$ e poiché gli addendi in$s_{n_{1}}$ sono tutti $\leq$ di quelli di $s_{n_{2}}$ posso applicare il teorema del confronto alle successioni $s_{n_{1}}$ e $s_{n_{2}}$
>	Quindi $0\leq \sum_{i=0}^\infty{a_{n}}=\sum_{i=0}^{n_{0}-1}{a_{i}}+\sum_{i=n_{0}}^\infty{a_{i}}\leq\sum_{i=0}^{n_{0}-1}{a_{i}}+\lim_{ n \to \infty } {s_{n_{2}}}$
>	Se $\lim_{ n \to \infty } {s_{n_{2}}}$ esiste ed è finito
>2. Segue direttamente da 1. è l'opposto