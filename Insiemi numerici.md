---
tags: [analisi_1]
---
[[Insieme]]

I vari insiemi numerici sono:
	• [Naturali] -> $\{0,1,2,3,4,... \in N\}$ 
	• [Relativi] -> $\{N \cup N*(-1) \in Z\}$
	• [Razionali] -> $\{a,b\not=0 \in Z \text{ | } \frac{a}{b} \in Q\}$
	• [Reali] -> DOPO
	• [Complessi] -> $\{ a + bi | a,b \in \mathbb{R}, i^{2} = -1 \}$

## Proprietà di R e Q

1 • Sia $E\subseteq R$ superiormente limitato e sia $l = sup(E)$ allora 
```math
||{"id":269946290256}||

\forall\epsilon\gt0, \exists x \in E \text{ | } l - \epsilon \lt x
```
>[!INFO]- Dimostrazione
>supponiamo per assurdo che $\forall x \in E \text{ si abbia } x \le l - \epsilon$  allora $l - \epsilon$ è un maggiorante di E ma $l - \epsilon \le l$ e $l$ è il minimo dei maggioranti, quindi è un assurdo

2 • R è Archimedeo, cioè $\forall x,y \in R \text{ con } x,y\gt 0, \exists n \in N \text{ | } n*x \gt y$

>[!INFO]- Dimostrazione
>Per assurdo siano $x,y \gt 0 \text{ | } \forall n \in N \text{ si abbia } y \ge xn$ 
>Consideriamo l'[[insieme]] $Y = \{nx\text{ | }n \in N\}$, allora per ipotesi, Y è superiormente limitato con $\overline{y} = sup(Y)$ quindi $\forall n \in N, \overline{y} \ge nx$ e quindi vale anche che $\forall m \in N \text{ si ha che } \overline{y} \ge (m + 1)x$ 
>Allora $\overline{y} = mx +x$, cioè $\overline{y} -x = mx$ e questo è vero $\forall m$, quindi anche $\overline{y} -x$ è maggiorante di Y, inoltre visto che $x \gt 0 \text{ si ha che } \overline{y} -x \lt \overline{y}$ che è assurdo perché $\overline{y}$ dovrebbe essere il minimo dei maggioranti

3 • Q è denso in se cioè
```math
||{"id":805190336532}||
\forall x,y \in Q \text{ | } x \lt y, \exists z \in Q \text{ | } x \lt z \land z \lt y

```

>[!INFO]- Dimostrazione
>basta prendere $\frac{xy}{2} \in Q$

4 • Q è denso in R cioè $\forall x,y \in R \text{ | } x \lt y, \exists z \in Q \text{ | } x \lt z \lt y$ 
