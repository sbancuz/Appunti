---
tags: [analisi 1]
---

Siano $\{{a_{n}}\}_{n\in N}$ e $\{{b_{n}}\}_{n\in N}$ non definitivamente negative e sia $a_{n}\sim b_{n},n\to \infty$ allora: $\sum a_{n}$ e $\sum b_{n}$ hanno lo stesso carattere

>[!note]- Dimostrazione
>Sappiamo che $\lim_{ n \to \infty } {\frac{a_{n}}{b_{n}}}=1$ e quindi $\forall {\epsilon} > {0}, \exists {n_{0}}$ tale che $\forall {n} \geq {n_{0}}$ ho che $-\epsilon<\frac{a_{n}}{b_{n}}-1< \epsilon$
>Se scelgo $\epsilon = \frac{1}{2}$ ho che $\exists {n_{0}}$ tale che $\forall {n} \geq {no}$ ho che $\frac{1}{2}< \frac{a_{n}}{b_{n}}< \frac{3}{2}$.
>
>Ora posso applicare il teorema del confronto alle 3 successioni.
>Se $\sum_{i=0}^\infty{b_{n}}$ converge allora $\sum_{i=0}^\infty{a_{n}}$ converge, se $\sum_{i=0}^\infty{a_{n}}$ diverge allora $\sum_{i=0}^\infty{b_{n}}$ diverge