---
tags: [analisi_1]
---
• Invertibilità
La funzione $f: R\to R$ non è biunivoca però se cambio dominio e codominio posso ottenere una funzione biunivoca (ci sono infiniti modi per prendere dominio e codominio)
```math
||{"id":1580579863823}||
f:x\to sen(x)

```
Convenzionalmente si considera come  $D \in[-\frac{\pi}{2}, \frac{\pi}{2}]$ e $Codo \in [-1,1]$ e la sua inversa sarà 
```math
||{"id":889902629767}||

asen(x):[-1,1]\to[-\frac{\pi}{2}, \frac{\pi}{2}]
```
>[!info]
>$sen(asen(x)) = x \text{ se } x\in D_{asen}$

• Simmetrie
Sia $A\subseteq R$ simmetrico rispetto O, allora $f:R\to R$ si dice
	• [pari] -> $\forall x\in A$ si ha che $f(-x) = f(x)$
	• [dispari] -> $\forall x\in A$ si ha che $f(-x) = -f(x)$

```math
||{"id":1611805503908}||


```


Ogni $f:R\to R$ può essere scritta in modo univoco come somma di $f$ pari e $f$ dispari

>[!note]- Dimostrazione
> $f:R\to R$ allora $f(x) = \frac{f(x)+f(-x)}{2} + \frac{f(x)-f(-x)}{2}$
> se chiamo $p(x) = \frac{f(x)+f(-x)}{2}$ e $d(x) = \frac{f(x)-f(-x)}{2}$
> allora $p(x)$ è pari e $d(x)$ è dispari, adesso provo l'unicità
> Siano $p(x)$ e $\overline{p}(x)$ pari e $d(x)$ e $\overline{d}(x)$ dispari tc
> $$\left\{\begin{align}f(x) &= p(x) + d(x)\\ f(x) &= \overline{p}(x) + \overline{d}(x) \end{align}\right\|$$
> Allora abbiamo che $p(x)- \overline{p}(x) = d(x)- \overline{d}(x)$, ma a sx è pari e a dx è dispari allora l'unico modo che sia possibile è $0=0$ quindi sono uguali

• Limitata
$f:R\to R$ si dice LIMITATA se la sua $Im(x)$ è limitata, ovvero $\exists M\in R, M\gt 0 \text{ | } \forall x \in R \text{ si ha } -M\le f(x)\le M$
	• se  $\exists M\in R, M\gt 0 \text{ | } \forall x \in R \text{ si ha } -M\le f(x)$ allora si dice superiormente limitata
	• se  $\exists M\in R, M\gt 0 \text{ | } \forall x \in R \text{ si ha }  f(x) \ge M$ allora si dice inferiormente limitata

• Monotonia
$f:R\to R$ si dice MONOTONA crescente se $\forall a,b \in R$ si ha che $a\le b \to f(a)\le f(b)$ quindi $f$ conserva il verso delle disequazioni. 
Si dice strettamente monotona crescente se $a\lt b \to f(a)\lt f(b)$

$f:R\to R$ si dice MONOTONA decrescente se $\forall a,b \in R$ si ha che $a\le b \to f(a)\ge f(b)$ quindi $f$ conserva il verso delle disequazioni. 
Si dice strettamente monotona decrescente se $a\lt b \to f(a)\gt f(b)$

>[!info]
>La composizione di $f$ crescenti è crescente
>La composizione di $f$ decrescenti è decrescente
>
>Una $f$ strettamente monotona è iniettiva, ma non il contrario eg: $f(x)=\frac{1}{x}$
>>[!note]- Dimostrazione
>>WLOG si ha $f:R\to R$ crescente provo che $f$ è iniettiva,
>>siano $a,b \in R, a\not=b$ allora $f(a)\not=f(b)$
>
>Sia $f:R\to R$ strettamente monotona e suriettiva, allora è invertibile e $f^{-1}$ sarà strettamente monotona

• Periodicità
 $f:R\to R$ si dice periodica di periodo $T\in R, T\gt 0$ se $\forall x\in R, f(x+T) = f(x)$
 e T è il minimo reale positivo con questa proprietà e $I=[x_0,x_0+T)$ è un intervallo di periodicità per $f$. Se $f$ è periodica non è invertibile in quanto non è iniettiva.
 
 




