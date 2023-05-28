---
tags: analisi_2
---

==>[[Funzioni a più variabili]]

### Limiti

Siano $A\subseteq \mathbb R^n$ aperto, $\underline{x}_{0}\in A$ e $f$ una funzione a valori reali definita su $A$.
Diciamo che $f$ tende al limite $l\in \mathbb{R}$ per $\underline{x}$ che tende a $\underline{x}_{0}$ e scriviamo
$$
\lim_{ \underline{x} \to \underline{x}_{0} } {f(\underline{x})} = l
$$
se e solo se $\forall {\epsilon}> 0 {}$ esiste $\delta>0$ tale che $|f(\underline{x} - l)|<\epsilon$ per ogni $\underline{x}\in B_{\gamma}(\underline{x}_{0})\setminus \{ \underline{x} _{0}\}$

>[!note]
>Valgono le stesse proprietà del caso ad una variabile

### Differenze con il caso n=1

In $n =1$ ci sono 2 modi per avvicinarci a $x_{0}$, invece per $n>1$ abbiamo invece infiniti modi per avvicinarci ad un vettore

### Calcolo del limite

Per calcolare il limite (se esiste) basta azzerare tutte le variabili a parte una e calcolare quel limite, poi questo processo si ripete per ogni variabile. Per il teorema dell'unicità del limite se i risultati dei vari limiti sono uguali allora quello sarà il limite di $f(\underline{x})$

### Maggiorazioni con funzioni radiali

Sia $\underline{x}_{0}\in A\subseteq \mathbb{R}^{n}$ con $A$ aperto e sia $f$ una funzione a valori reali definita almeno su $A\setminus \{ \underline{x}_{0} \}$ e sia $l\in\mathbb{R}$.
Se esiste un $g:(0,\infty)\to \mathbb{R}$ tale che $g(r)\to_{0}$ per $r\to_{0}$ e $|f(\underline{x}) -l|\leq g(|\underline{x}-\underline{x}_{0}|)$ allora
$$
\lim_{ \underline{x} \to \underline{x}_{0} } {f(\underline{x})} = l
$$