---
tags: [meccanica]
---
Si dice meccanismo quando ho che $\#GDV<\#GDL \implies \text{isostatico}$

```math
||{"id":363479437171}||





```
Per A si trova più facile usare l'angolo relativo all'estensione di $\overline{OA}$

```math
||{"id":307919535159}||

```
$$
\begin{align}
ae^{i\alpha}+be^{i\beta}= & ce{ ^{i\gamma} } \\
\frac{d}{dt} \implies ia\dot{\alpha}e^{i\alpha}+ib \dot{\beta}e^{i\beta} = & ic\dot{\gamma}e^{i\gamma}+\dot{c}e^{i\gamma}
 
\end{align}
$$
$$
\left\{
\begin{align}
a\cos\alpha+b\cos\beta= & c\cos\gamma =x_{B}\\
a\sin\alpha+b\sin\beta= & c\sin\gamma =y_{B}\\
\end{align}
\right|
$$
$$
\frac{d}{dt} \implies\left\{
\begin{align}
-a\dot{\alpha}\sin\alpha-b\dot{\beta}\sin\beta= & -c\dot{\gamma}\sin\gamma + \dot{c}\cos\gamma=\dot{x}_{B}\\
-a\dot{\alpha}\cos\alpha-b\dot{\beta}\cos\beta= & -c\dot{\gamma}\cos\gamma + \dot{c}\sin\gamma=\dot{y}_{B}\\
\end{align}
\right|
$$
```math
||{"id":1127647562318}||
\frac{d^{2}}{d^{2}t} \implies
&&	a\ddot{\alpha }\sin\alpha -a\dot{\alpha }^{2}\cos\alpha -b\ddot{\beta}\sin\beta - b\dot{\beta }^{2}\cos\beta =  \ddot{x}_{B}
&&	a\ddot{\alpha }\cos\alpha -a\dot{\alpha}^{2}\sin\alpha + b\ddot{\beta }\cos\beta - b\dot{\beta }^{2}\sin\beta =  \ddot{x}_{B}

```

>[!tip]
>I primi 2 termini definiscono l'accellerazione della terna di rifermimento detta accelerazione di trascinamento
>
>Negli altri 2 è come se studiassi il moto solo della seconda asse detta accelerazione relativa

Da qua si possono derivare i vincoli per la cinematica inversa.

### Manovellismo ordinario centrato

Per il corretto funzionamento di questo meccanismo di deve avere che $\overline{AB} > \overline{OA}$ e $B$ è sulla stessa asse di $O$

```math
||{"id":993535526145}||


```


La rappresentazione vettoriale è la stessa di prima solo che $\gamma = 0$
$$
ae^{i\alpha} +be^{i\beta} = c
$$
$$
\left\{
\begin{align}
a\cos\alpha+b\cos\beta= & c=x_{B}\\
a\sin\alpha+b\sin\beta= & 0 =y_{B}\\
\end{align}
\right|
$$
$$
\frac{d}{dt} \implies\left\{
\begin{align}
-a\dot{\alpha}\sin\alpha-b\dot{\beta}\sin\beta= & \dot{c}=\dot{x}_{B}\\
-a\dot{\alpha}\cos\alpha-b\dot{\beta}\cos\beta= & 0=\dot{y}_{B}\\
\end{align}
\right|
$$
$$
\frac{d^{2}}{d^{2}t} \implies\left\{
\begin{align}

a\ddot{\alpha }\sin\alpha -a\dot{\alpha }^{2}\cos\alpha -b\ddot{\beta}\sin\beta - b\dot{\beta }^{2}\cos\beta =\ddot{c}=  \ddot{x}_{B}\\
a\ddot{\alpha }\cos\alpha -a\dot{\alpha}^{2}\sin\alpha + b\ddot{\beta }\cos\beta - b\dot{\beta }^{2}\sin\beta = 0= \ddot{y}_{B} \\
\end{align}

\right|
$$