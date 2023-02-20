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
