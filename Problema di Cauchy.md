---
tags: [analisi_2]
---
Data una EDO di ordine n in forma normale per in un dato intervallo $I\subset \mathbb R$ , data una funzione $f$ con dominio $A \subset \mathbb R^{n}$ e un punto generico. Si dice problema di Cauchy associato alla EDO il problema che consiste nel determinare una soluzione $y:J \to \mathbb R$ della EDO
per un intervallo $J \subseteq I$  tale che $t_{0} \in J$ che soddisfi il sistema
$$
\begin{cases}
y^{(n)}(t) = f(t,y(t),y'(t),t''(t),\dots,y^{(n-1)}(t))  &  t \in J\\
y(t_{0}) = y_{0}, \\
y'(t_{0}) = y_{1}' \\
\vdots \\
y^{(n)}(t_{0}) = y_{0}^{(n)}
\end{cases}
$$
>[!info]
>Nel problema di Cauchy servono tante equazioni quante costanti presenti nell'integrale generale della EDO e quindi il numero delle soluzioni è $\infty^{n}$ per un sistema a n variabili

### Risoluzione

#### Passo I
Determinare l'integrale generale della EDO

### Passo II
Sostituiamo l'integrale generale nel sistema delle n condizione e determiniamo le constanti $c_{1},c_{2},c_{3},\dots,c_{n}$ 

#### Passo III
Sostituiamo il valore delle constanti nell'integrale generale

>[!note] Esempio
>$$
>\begin{cases} 
> y'(y) = \frac{1}{t}  & t > 0 \\
> y(2) = 0
>\end{cases}
>$$
>
>Passo I => $y(t)=\ln t+c$ con $c \in \mathbb R$
>
>Passo II => Impongo condizione $0 = y(2) = \ln_{2} +c \implies c=-\ln_{2}\in \mathbb R$
>
>Passo III => La soluzione particolare del problema di Cauchy è $y(t)=\ln t-\ln_{2}$

Nel caso ci siano soluzioni costanti è facile trovarle. Data una EDO del primo ordine in forma normale per un intervallo $I\subseteq \mathbb R$, una soluzione costante è una funzione $y(t)=c$ per ogni $t\in I$ e $c \in \mathbb R$ che è soluzione. Siccome per ogni $c \in \mathbb R, (c)' = 0$ allora abbiamo necessariamente che  $f(t,c) =0, \forall {t}  {}$ 

### Cauchy per [[EDO lineari]]

Sia un sistema di Cauchy definito con un EDO lineare
$$
\begin{cases}
y'(t) = a(t)y(t) + b(t) \\
y(t_{0}) = y_{0}
\end{cases}
$$
allora si ha che esiste un'unica soluzione $y$ su tutto $I$ per il problema di Cauchy

>[!warning]
>Questo teorema vale solo se a,b sono continue

### Cauchy per EDO del secondo ordine lineare

Data una EDO del secondo ordine lineare è un equazione della forma:
$$
a(t)y''(y)+b(t)y'(t)+c(t)y(t)=f(t)
$$
dove $a,b,c,d:I\subseteq \mathbb R\to \mathbb R$ e $a\neq 0$, e assegnati $t_{0}\in I$ e $y_{0},z_{0}\in \mathbb R$ si chiama problema di Cauchy associato il problema di determinare una funzione $y:I\subseteq J\to \mathbb R$ che soddisfa il sistema 
$$
\begin{cases}
a(t)y''(y)+b(t)y'(t)+c(t)y(t)=f(t) \\
y(t_{0}) = y_{0} \\
y'(t_{0}) = z_{0}
\end{cases}
$$
>[!note]
>L'integrale generale della EDO di secondo ordine è una famiglia di infinite soluzioni, quindi abbiamo bisogno di 2 condizioni per il secondo ordine


### Cauchy per SDL

Dato un SDL 
$$
\underline{y}'(x) = A(x)\underline{y}(x)+\underline{b}(x)
$$
si chiama problema di Cauchy associato. il sistema
$$
\begin{cases}
\underline{y}'(x) = A(x)\underline{y}(x)+\underline{b}(x) \\
\underline{y}(x_{0})=\underline{y}_{0}
\end{cases}
$$
