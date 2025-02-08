---
tags:
  - logica_algebra
---
Finora abbiamo studiato [[Logica modale]] con un solo connettivo modale $1$-ario $\square$. Adesso consideriamo le logiche con più di un connettivo modale e connettivi modali $n$-ari. La semantica dei connettivi modali $n$-ari si definisce come: Sia $S$ un insieme, $R \subseteq \underbrace{ S \times \dots S }_{ n + 1\text{ volte} }$  una relazione $(n+1)$-aria su $S$ e un modello $M$ su $(S,R)$. Sia $w\in S$
$$
M \vDash _{w}\square (F_{1}, \dots, F_{n})
$$
sse per ogni $v_{1}\in S, \dots, v_{n}\in S$ tali che $(w, v_{1},\dots,v_{n})\in R$ si ha che
$$
M \vDash _{v_{1}} F_{1}, \dots, M \vDash _{vn} F_{n}
$$
### Logiche temporali

Queste logiche hanno $3$ connettivi modali $1$-ari.
1) $X \implies$ *next state*
2) $F \implies$ *sono future state*
3) $G \implies$ *all future states*
e $3$ connettori $2$-ari
1) $U\implies$ *until*
2) $R\implies$ *release*
3) $W \implies$ *weak until* 

## Da finire se ho voglia dopo esame