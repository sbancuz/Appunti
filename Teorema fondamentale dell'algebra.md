Ogni polinomio a coefficienti complessi ammetta almeno una radice

### Corollario

Se $p(z) = a_nz^n+a_{n-1}z^{n-1}+...+a_0z^0$ è un polinomio di grado n a coefficienti in $C$ allora possiede esattamente n radici complesse (non necessariamente distinte) e $p(z)=a_n(z-r_1)(z-r_2)...(z-r_n)$

>[!note]- Dimostrazione
>Segue dal Teorema di ruffini, infatti per il teo fondamentale $p(z)$ ha una radice $r_1$, allora per Ruffini $p(z)$ è divisibile per $(z-r_1)$, quindi $\frac{p(z)}{z-r_1}$ è un polinomio e se ha grado > 0 si può applicare lo stesso ragionamento

Se nella fattorizzazione la rafice $r_i$ compare $\alpha$ volte si dice che $r_i$ ha molteplicità $\alpha$
$p(z)=a_n(z-r_1)^{\alpha_1}(z-r_2)^{\alpha_2}...(z-r_m)^{\alpha_m}$ dove $\alpha_1 + \alpha_2 + ... + \alpha_m = n$

> [!info] Teorema
Sia $p(x)$ un polinomio a coefficienti reali, se $r\in C$ è una radice di $p(x)$, allora anche $\overline{r}$ (coniugato) lo sarà 


## Corollario

Ogni polinomio a coefficienti reali si fattorizza come prodotto di termini di I o II grado, infatti se una radice è reale non c'è problema, ma se è complessa allora $x-r$ non è a coefficienti reali però $p(x)$ è divisibile anche per $x-\overline{r}$, quindi $p(x)$ è divisibile per $$(x-r)(x-\overline{r})=x^2-\overline{r}x-rx+|r|^2=x^2-x(r-\overline{r})+|r|^2=x^2-2x*\Re(r)+|r|^2$$
## Corollario

Un polinomio a coefficienti reali di grado dispari ha almeno una radice reale.

>[!note]- Dimostrazione
>$p(x)$ non può avere solo fattori reali di II grado, quindi ha un fattore lineare $x-r, r\in R$

