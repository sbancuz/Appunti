Una funzione è una terna formata da:
	1 • [[Insieme]] Dominio
	2 • [[Insieme]] Codominio
	3 • Una relazione $R \subseteq AxB$ tc 	
```math
||{"id":515579115614}||
\forall a \in A, \exists b \in B \text{ | } (a,b) \in R 

```
```math
||{"id":1036866679603}||
\forall a\in A, \forall b, \overline{b} \in B, \text{ se } (a,b)\in R \land (\overline{b}, a)\in R \text{ allora } b = \overline{b}

```

Se metto assieme le due relazioni significa che ogni elemento del dominio deve essere in relazione con un solo elemento del dominio.

Le funzioni si definiscono $$f:A\to B \text{ e f(a) = b} $$
Si definisce l'immagine di una funzione come $$Im(f):=\{y\in B \text{ | }\exists x \in A, f(x) = y\}$$
Le funzioni che $f:N\to R$ sono dette [[Successioni]]
Le funzioni che $f:R\to R$ sono dette di variabili reali

## Iniettività

Sia $f:A\to B$ si dice che $f$ è iniettiva se ogni elemento del codominio ha al più un elemento una controimmagine ovvero se $x \not= \overline{x} \to f(x) \not= f(\overline{x})$
```math
||{"id":718516305693}||


```

## Suriettività

Sia $f:A\to B$ si dice che $f$ è suriettiva se ogni elemento del codominio ha almeno una controimamgine ovvero $\forall y \in B \text{ | } \exists x \in A \text{ tc } f(x) = y$ 

## Biiettiva

Se è sia iniettiva e suriettiva.

## Composizione

Se $f:A\to B$ e $g:B \to C$ allora si può definire la funzione $$\begin{align}g•f: A&\to C\\x&\to g(f(x))\end{align}$$
Quest'operazione non è commutativa $g•f \not= f•g$

## Invertiblità

Sia  $f:A\to B$ si dice che f è invertibile sse $\exists g:B\to A \text{ | } \left\{\begin{align}g•f = i_a \\ f•g = i_b\end{align}\right|$ in tal caso $g$ si dice inversa di $f$, se $f$ è biiettiva allora sarà invertibile

>[!info] 
>L'inversa se esiste è unica e può anche essere inversa di se stessa

Sia $f:A\to B$ qualunque, se $y \in B$ indico con $$f^{-1}(y) = \{x\in A \text{ | }f(x) = y\}$$
l'insieme delle controimmagini di y $f^{-1}$ è un sottoinsieme del dominio.
Affinche $f$ sia invertibile, si deve avere che la corrispondenza che associa ad un elemento del codominio gli elementi della controimmagine sia una funzione

>[!note]
>$f:x\to x^2$, $f^{-1}(-4) = \emptyset$ $f^{-1}(4) = \{-2, 2\}$
>Quindi $f$ di sicuro non è invertibile

Il grafico si una $f^{-1}$ è dato dal grafico di $f$ specchiato per la bisettrice del I e del III quadrante

```math
||{"id":1162987273954}||


```
Tenendo la $f(x) =x^2$ ma cambiando il dominio in $f:R^+ \to R^+$ la posso far diventare biunivoca

![[Proprietà delle funzioni]]

