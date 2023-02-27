---
tags: [analisi_1]
---

Sia $\{{a_{n}}\}_{n\in N}$ una successione non negativa, se esiste il $\lim_{ n \to \infty } {\sqrt[n]{ a_{n} }}$ allora 
	• se $l<1$, $\sum_{i=0}^\infty{a_{i}}$ converge
	• se $l>1$, $\sum_{i=0}^\infty{a_{i}}$ diverge
	• se $l=1$ non si sa

>[!note]- Dimostrazione
> Sia $\lim_{ n \to \infty } {\sqrt[n]{ a_{n} }}<1$ allora $\forall {\epsilon} \geq {0}, \exists {n_{0}} \text{ tale che } \forall {n} \geq {n_{0}}$, $l-\frac{\epsilon}{2}<\sqrt[n]{ a_{n} }<l+\frac{\epsilon}{2}$ e quindi $\sqrt[n]{ a_{n} }<(1-\epsilon)+\frac{\epsilon}{2}=1+\frac{\epsilon}{2}$ 
> Allora $a_{n}<\left( 1-\frac{\epsilon}{2} \right)^n$ che converge e per il teorema del confronto anche $\{{a_{n}}\}_{n\in N}$ convergerà