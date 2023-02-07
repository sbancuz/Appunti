## Confronto locale 

Siano $f,g:[a,b]\to R$ e $x_{0}\in (a,b)$, si dice che $f$ è un $O(g)$ e si scrive $f=O(g)$, se $\exists {M} \in {R}$ e un intorno $I_{x_{0}}$ di $x_{0}$ tale che $\forall {x} \in {I_{x_{0}}}$ si ha 
$$
|f(x_{})|\leq M\leq|f(x)|
$$

Se esiste $\lim_{ x \to x_{0} } {\frac{f(x_{})}{g(x)}}=l\in R$ allora $f=O(g)$

Nelle stesse ipotesi di prima si dice che $f$ è un o-piccolo di $g$ in simboli $f=o(g)$
Se esiste $h:[a,b]\to R$ tale che $f(x)=g(x)h(x)$ e $\lim_{ x \to x_0 } {h(x)}=0$
Se esiste $\forall {x} \in {I_{x_{0}}}$ $\lim_{ x \to x_{0} } {\frac{f(x_{})}{g(x)}}=0$

> [!NOTE]
> Si dice anche che $f$ è un infinitesimo di ordine inferiore a $g$
> 

## Formula di Taylor

Voglio approssimare localmente una funzione con un polinomio, cioè data $f:[a,b]\to R$ e $x_{0}\in (a,b)$ cerco $P_{n}(x)$ di grado $n$ tale che per $x\to x_{0}$, $f(x)-P_{n}(x)=o((x-x_{0})^n)$

### Lemma 1

$\forall n \in N$ tale che $D^{n-1}((x-x_{0})^n)=n!(x-x_{0})$ dove $D$ è la derivata

>[!note]- Dimostrazione
>Per induzione su n:
>1. $n=1$ -> $D^0((x-x_{0})^1)=x-x_{0}=1!(x-x_{0})$
>2. $D^{m}((x-x_{0})^{m+1})=D^{m-1}((x-x_{0})^m)=(m+1)m!(x-x_{0})$

### Lemma 2

Sia $f:[a,b]\to R$ continua in $x_{0}$ con derivate continue in $x_{0}$ fino all'n-esima allora
$$
\lim_{ x \to x_{0} } \frac{{f(x_{})}}{(x-x_{0})^n}= 0\text{ sse } f(x_{0})=f'(x_{0})=\dots=f^{(n)}(x_{0})=0
$$
## Teorema di Taylor con resto di Peano

Sia $f:[a,b]\to R$, $x_{}\in [a,b]$ continua e derivabile con continuità n volte in $x_{0}$, sia $P_{nx_{0}}(x)$ il polinomio così definito
$$
P_{nx_{0}}(x)= \sum_{i=0}^{n}{\frac{f^{(i)}(x_{0})}{i!}}(x-x_{0})^i
$$
E si ha che $f(x)-P_{nx_{0}}(x) = o((x-x_{0})^n)$ 

$P_{nx_{0}}(x)$ si chiama polinimio di Taylor di grado $n$ di $f(x)$ in $x_{0}$, se poi $x_{0}=0$ allora sarebbe il polinomio di MacLaurin  

>[!note]- Dimostrazione
>Devo provare che $\lim_{ x \to x_{0} } \frac{{f(x)-P_{nx_{0}}(x)}}{(x-x_{0})^n}=0$ che per il lemma 2 vale a dire che $f(x)-P_{nx_{0}}(x)=0$
>Sia $0\leq k\leq n$
>$$\begin{align}
>&D^{(k)}(f(x_0)-P_{nx_{0}}(x))(x_{0}) = f^{(k)}(x_{0})- D^k\left( {\frac{f^{(k)}(x_{0})}{k!}}(x-x_{0})^k \right)(x_{0}) \\
&=f^{(k)}(x_{0})-\frac{1}{k!}f^(k)(x_{0})k!= 0
\end{align}
>$$

![[Espansioni di Taylor MacLaurin notevoli]]
