---
tags: [analisi_1]
---
Sia $a=\{{a_{n}}\}_{n\in N}$ convergente, $\lim_{ n \to \infty } {a_{n}}=l$ e sia $\{{a_{n}}\}_{n\in N}$ definitivamente $\ge 0$ allora $l\ge 0$

>[!note]- Dimostrazione
> Sia $l=\lim_{ n \to \infty } {a_{n}}$, allora $\forall\epsilon\gt 0 ,\exists n \in N ,\forall {n} \ge {n_{0}}$ si ha $|a_{n}-l|\le\epsilon$, inoltre posso scegliere $n_{0}$ in modo tale che $a_{n}\ge 0$
> Quindi abbiamo che $\forall {\epsilon} \ge {0},\forall {n} \ge {n_{0}}$ si ha $0\le a_{n}\le l+\epsilon$
> Ora, se $l$ fosse $< 0$, potrei prendere $\epsilon$ compresa tra 0 e $-l$ e avrei che $l+\epsilon \lt 0$ da cui $0\le a_{n} \le l+\epsilon\le 0$ che è un assurdo, quindi $l\ge 0$
> 
