## Teorema degli zeri

Sia $f:[a,b]\to R$ continua in $[a,b]$ e tale che $f(a)f(b)<0$ allora $\exists {c} \in {(a,b)}$ tale che $f(c)=0$, se poi $f$ è strttamente monotona, allora il punto $c$ è unico
```math
||{"id":781248353629}||


```
>[!note]- Dimostrazione
>Idea: Costruire una successione che tenda a $c$
>
>Poniamo $a_{0}=a$ e $b_{0}=b$, sia poi $c_{1}=\frac{a_{0}+b_{0}}{2}$, adesso ho 3 possibilità:
>	1. $f(c_{1}) = 0$ ho finito
>	2. $f(a_{0})f(c_{1})<0$, allora si pone $a_{1}=a_{0}$ e $b_{1}=c_{1}$
>	3. $f(b_{0})f(c_{1})<0$, allora si pone $a_{1}=c_{1}$ e $b_{1}=b_{0}$
>	4. $c_{2}=\frac{a_{1}+b_{1}}{2}$
>
>E si ripete, in questo modo restano le successioni $\{{a_{n}}\}_{n\in N}$ e $\{{b_{n}}\}_{n\in N}$ che rispettano:
>	1. $\{{a_{n}}\}_{n\in N}$ è crescente e superiormente limitata
>	2. $\{{b_{n}}\}_{n\in N}$ è decrescente e inferiormente limitata
>	3. $b_{n}-a_{n}\leq \frac{b-a}{2^n}$
>	4. per costruzione $f(a_{n})f(b_{n})<0$
>
>Inoltre $\lim_{ n \to \infty } {b_{n}-a_{n}}\leq\lim_{ n \to \infty } {\frac{b-a}{x^n}}=0$
>
>Poi $f$ è continua in $[a,b]$, quindi $\lim_{ n \to \infty } {f(a_{n})f(b_{n})}=f(l)^2$.
>
>Infine per la permanenza del segno si ha $\lim_{ n \to \infty } {f(a_{n})f(b_{n})}\leq 0$, dunque $f(l)^2\leq0$ e visto che è un quadrato $f(l)=0$
>
>Se poi $f$ è monotona, allora è iniettiva, quindi $f$ si annulla al più una volta

## Teorema di Weierstrass

Sia $f:[a,b]\to R$ continua sull'intervallo chiuso e limitato $[a,b]$, allora $f$ assume massimo e minimo in $[a,b]$ cioè $$
\forall {x} \in {[a,b]} \text{ tale che} f(m)\leq f(x)\leq f(M) 
$$
dove m,M sono minimo e massimo di $f$ in $[a,b]$

>[!warning]
>Le ipotesi del teorema sono tutte necessarie

## Teorema dei valori intermedi

Sia $f$ continua su $[a,b]$, siano m e M minimo e massimo di $f$ su $[a,b]$, e sia $t$ tale che $m\leq t\leq M$, allora $\exists {x_{0}} \in {[a,b]}$ tale che $f(x_{0})=t$

>[!note]- Dimostrazione
>Abbiamo $t$ tale che $m\leq t\leq M$ per $W$.
>
>Siano $x_{m}$ e $x_{M}$ tali che $f(x_{m})=m$ e $f(x_{M})=M$ allora consideriamo la funzione $g(x)=f(x)-t$ che è continua in tutto $[a,b]$ e a maggior ragione è continua in $[x_{m},x_{M}]$
>
>Abbiamo $g(x_{m})=f(x_{m})-t=m-t\leq 0$ e $g(x_{M})=f(x_{M})-t=M-t\geq 0$
>
>Per il teorema degli zeri $\exists {c} \in {[x_{m},x_{M}]}$ tale che $g(c)=0$ quindi $g(c)=f(c)-t=0$, cioè $f(c)=t$

## Conseguenze

$\forall {y} \in {R},y>0$ e $n>1 \in N$ esiste ed è unico $x>0 \in R$ tale che $x^n=y$ cioè esiste un unica radice aritmetica n-esima di un numero positivo.

## Inversa di una funzione continua

Sia $f:I\to R$ con $I$ intervallo qualunque continua in $I$, allora $f$ è invertibile sse $f$ è strettamente monotona, inoltre anche $f^{-1}$ è strettamente monotona e continua

>[!note]- Dimostrazione
>Abbiamo già visto che se $f$ è strettamente monotona, allora è invertibile
>
>Allora sia $f$ continua e invertibile, proviamo che sia monotona
>
>Per assurdo, non sia strettamente monotona, quindi $\exists {x_{1},x_{2},x_{3}} \in {I}$ tali che $x_{1}<x_{2}<x_{3}$ ma $f(x_{1})<f(x_{2})$ e $f(x_{2})>f(x_{3})$ o $f(x_{1})>f(x_{2})$ e $f(x_{2})<f(x_{3})$
>
>Per il teorema dei valori intermedi $\exists {x_{0}} \in {(x_{1},x_{2})}$ tale che $f(x_{0})=f(x_{3})$, ma $x_{0}\neq x_{3}$ che è assurdo perché $f$ è invertibile e quindi iniettiva
>
>Resta da vedere se anche $f^{-1}$ è continua
>
>Ma, se $f$ è strettamente monotona, sappiamo già che $f^{-1}$ è strettamente monotona, quindi per il teorema di monotonia o è continua o ha discontinuità a salto.
>
>Ma se ha discontinuità a salto, la sua immagine non è un intervallo, assurdo poiché l'immagine di $f^{-1}$ è $I$

