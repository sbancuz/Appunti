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
\begin{align}
\sum_{j}\overrightarrow{C_{jo}} & =J_{o}\overrightarrow{\dot{\omega}} = \sum_{j}(p_{j}-o)\land \overrightarrow{F_{j}}=(J_{G}+Mr^{2})\overrightarrow{\dot{\omega}} = J_{G}\overrightarrow{\dot{\omega}}+Mrr\overrightarrow{\dot{\omega}}  \\
 & = J_{G}\overrightarrow{\dot{\omega}}+(G-o)\land M\overrightarrow{a}
\end{align}
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
$$
\begin{align}
\frac{dL}{dt} = W  & = \sum_{j}\overrightarrow{F}_{j}\times \overrightarrow{V}+\sum_{k}\overrightarrow{C}_{k}\times \overrightarrow{\omega}+\overrightarrow{F}_{IN}\times \overrightarrow{G}+\overrightarrow{C}_{IN}\times \overrightarrow{\omega}_{IN}  \\
 & = \sum_{j}W_{j} + W_{IN} = 0 \implies \sum_{i} W+\sum_{i} W_{IN} = 0
\end{align}
$$

### Altro metodo per fare esercizi

$$
\sum\overrightarrow{F} = m \overrightarrow{a} = m \frac{d\overrightarrow{v}}{dt} \implies \sum\overrightarrow{v}\times \overrightarrow{F}=m\overrightarrow{v}\frac{d\overrightarrow{v}}{dt} 
$$
$$
\sum W= \frac{1}{2}m\frac{d}{dt} (\overrightarrow{v}\times \overrightarrow{v}) = \frac{d}{dt} \left( \frac{1}{2}m\overrightarrow{v}\times \overrightarrow{v} \right)=\frac{d}{dt} \left( \frac{1}{2}mv^{2} \right) 
$$
$$
 \sum W = \frac{d}{dt} E_C
$$
### Teorema di Konig
$$
E_{C} = \frac{1}{2}\int _{V}v_{p}^{2}\rho \, dv =\frac{1}{2}h\rho \int _{A}v_{p}^{2} \, dA = \frac{1}{2}Mv_{G}^{2}+\frac{1}{2}J\omega^{2}
$$
con $\overrightarrow{v_{p} } = \overrightarrow{v}_{G} + \overrightarrow{\omega}\land(P-G)$
$$
\frac{dE_{C}}{dt} = M\overrightarrow{v_{G}}\times \overrightarrow{a}_{G}+J_{g}\overrightarrow{\omega}\times\dot{\overrightarrow{\omega}} = -W_{IN} 
$$

![[Macchine ad un grado di libertà]]
