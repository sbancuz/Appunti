---
tags: [meccanica]
---
$$
\sum\overrightarrow{F} = m\overrightarrow{a}
$$
$$
\sum\overrightarrow{C}=J\overrightarrow{\dot{\omega}}
$$
### Principio di d'Alembert

$F_{IN}$ = Forza d'inerzia

$$
\sum\overrightarrow{F} = m\overrightarrow{a} \implies \sum_{j}\overrightarrow{F_{j}}-m\overrightarrow{a} = 0 \implies \sum_{j}\overrightarrow{F_{j}}+F_{IN} = 0
$$
Quest'equazione fa si che si possono risolvere i problemi della dinamica con le equazioni della [[statica]].
$$
\sum_{j}\overrightarrow{C_{jo}}=J_{o}\overrightarrow{\dot{\omega}} = \sum_{j}(p_{j}-o)\land \overrightarrow{F_{j}}=(J_{G}+Mr^{2})\overrightarrow{\dot{\omega}} = J_{G}\overrightarrow{\dot{\omega}}+Mrr\overrightarrow{\dot{\omega}} = J_{G}\overrightarrow{\dot{\omega}}+(G-o)\land M\overrightarrow{a}
$$
$$
 \sum_{j}(p_{j}-o)\land \overrightarrow{F_{j}} -J_{G}\overrightarrow{\dot{\omega}}-(G-o)\land M\overrightarrow{a} = 0
$$
Queste sono le equazioni di equilibrio dinamico.

### Principio dei lavori virtuali (PLV)

Q = Lagrangiana

Questa formula vale su ogni i-esimo corpo
$$
\delta L=\sum_{j}\overrightarrow{F_{j}}\land\delta \overrightarrow{P_{j}}+\sum_{k}\overrightarrow{C_{k}}\land\delta \overrightarrow{\theta}+\overrightarrow{F_{IN}}\land\delta \overrightarrow{G}+\overrightarrow{C_{IN}}\land\delta \overrightarrow{\theta} = 0
$$
$$
\delta L = Q(q)\delta q + Q_{IN}(q)\delta q = 0
$$
$$
Q_{IN}(q) = \sum_{i}\left( m_{i}a_{ix}\frac{\delta G_{x}}{\delta q} + m_{i}a_{iy}\frac{\delta G_{y}}{\delta q} + J_{i} \ddot{\theta_{i}} \frac{ \partial \theta_{i} }{ \partial q }   \right)
$$
