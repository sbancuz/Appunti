---
tags: analisi_2
---
Una EDO del secondo ordine lineare è un equazione della forma:
$$
a(t)y''(t)+b(t)y'(t)+c(t)y(t)=f(t)
$$
dove $a,b,c,d:I\subseteq \mathbb R\to \mathbb R$ e $a\neq 0$, nell'incognita $y:J\subseteq I\to \mathbb R$. Nel caso $f=0$ si parla di EDO omogenea se no completa.

### Integrale generale

L'integrale generale della EDO del secondo ordine è la famiglia di tutte le soluzioni dell'equazione in questione.

### [[Problema di Cauchy]]

### Teorema di esistenza e unicità globale per il problema di Cauchy

Dato il problema di Cauchy 
$$
\begin{cases}
a(t)y''(t)+b(t)y'(t)+c(t)y(t)=f(t) \\
y(t_{0}) = y_{0} \\
y'(t_{0}) = z_{0}
\end{cases}
$$
dove $a,b,c,d:I\subseteq \mathbb R\to \mathbb R$ continue e $a\neq 0$, e assegnati $t_{0}\in I$ e $y_{0},z_{0}\in \mathbb R$. Esso ammette un'unica soluzione $y(t) ,\forall {t\in I}  {}$

>[!note]
>Il teorema ci dice 3 cose importanti
>1) esiste una soluzione $y:J\subseteq I\to \mathbb R$
>2) la soluzione è unica
>3) $J=I$

### [[Principio di sovrapposizione]]

### Struttura dell'integrale generale delle EDO del secondo ordine lineare

Siano $a,b,c:I\subset \mathbb R\to \mathbb R$ continue con $a\neq 0$.

L'integrale generale dell'equazione omogenea è
$$
a(t)y''(t)+b(t)y'(t)+c(t)y(t)=0
$$
ed è uno [[Spazio vettoriale]] di dimensione 2, cioè le soluzioni sono tutte della forma
$$
y_{\sigma}(t) = c_{1}y_{\sigma,1}(t)+c_{2}y_{\sigma,2}(t)
$$
con $c_{1},c_{2}\in \mathbb R$, dove $y_{\sigma,1}$ e$y_{\sigma,2}$ sono le 2 soluzioni linearmente indipendenti

#### Dimostrazione

Dal principio di sovrapposizione deduciamo che l'insieme di tutte le soluzioni è uno spazio vettoriale.

Per dimostrare che la dimensione è 2 dobbiamo:

1) determinare 2 soluzioni linearmente indipendenti $y_{\sigma,1},y_{\sigma,2}$
Fissiamo $t_{0}\in I$ e scegliamo  $y_{\sigma,1}$ e $y_{\sigma,2}$ come soluzioni di 2 problemi di Cauchy, rispettivamente  $y_{\sigma,1}$ soluzione di
$$
\begin{cases}
a(t)y''(t)+b(t)y'(t)+c(t)y(t)=f(t) \\
y(t_{0}) = 1 \\
y'(t_{0}) = 0
\end{cases}
$$
e $y_{\sigma,2}$ soluzione di
$$
\begin{cases}
a(t)y''(t)+b(t)y'(t)+c(t)y(t)=f(t) \\
y(t_{0}) = 0 \\
y'(t_{0}) = 1
\end{cases}
$$
Tali soluzioni esistono uniche grazie al teorema di esistenza e unicità globale per il problema di Cauchy. Manca solo da verificare l'indipendenza lineare.

Per assurdo prendo $\exists {c} \neq {0}$  tale che $y_{\sigma ,{1}}(t) = cy_{\sigma,2}(t), \forall {t} \in {I}$. Allora per definizione di $y_{\sigma,1}$ e $y_{\sigma,2}$ abbiamo che 
$$
1=y_{\sigma,1}(t_{0}) = cy_{\sigma,2}(t_{0}) = c \times0 = 0
$$
che è una contraddizione.

2) verificare che ogni soluzione particolare si può scrivere come combinazione lineare di  $y_{\sigma,1}$ e $y_{\sigma,2}$
Sia $\overline{y}_{\sigma}$ una qualunque soluzione particolare della EDO, allora cerco $c_{1},c_{2}\in \mathbb R$ per cui $\overline{y}_{\sigma}$ coincide con la funzione 
$$
z(t)=c_{1}y_{\sigma,1}+c_{2}y_{\sigma,2}
$$
Scegliamo $c_{1}$ e $c_{2}$ in maniera tale che $\overline{y}_{\sigma} = z(t_{0})$ e $y'_{\sigma}(t_{0}) = z'(t_{0})$ ovvero
$$
\begin{cases}
\overline{y}_{\sigma}(t_{0}) = z(t_{0}) = c_{1}y_{\sigma,1}(t_{0})+c_{2}y_{\sigma,2}(t_{0}) = c_{1} \\
\overline{y}_{\sigma}'(t_{0}) = z'(t_{0}) = c_{1}y'_{\sigma,1}(t_{0})+c_{2}y'_{\sigma,2}(t_{0}) = c_{2} 
\end{cases}
$$
Per questa scelta di costanti la funzione diventa $y_{\sigma}(t) = y_{\sigma,1}(t)+y_{\sigma,2}(t)$. Concludiamo osservando che sia $z(t)$ che $\overline{y}_{\sigma}(t)$ soddisfano il problema di Cauchy
$$

\begin{cases}
a(t)y''(t)+b(t)y'(t)+c(t)y(t)=f(t) \\
y(t_{0}) = \overline{y}_{\sigma}(t_{0}) \\
y'(t_{0}) = \overline{y}'_{\sigma}(t_{0}) 
\end{cases}
$$
e quindi per il teorema di esistenza e unicità globale del problema di Cauchy abbiamo che $\overline{y}_{\sigma}(t)=z(t), \forall {t} \in {I}$ e questo conclude la dimostrazione.

### EDO del secondo ordine lineari omogenee a coefficienti costanti

Una EDO del secondo ordine lineare omogenea a coefficienti costanti è
$$
ay''(t)+by'(t)+cy(t)=0
$$
dove $a,b,c,d\in \mathbb R$  e $a\neq 0$

Si chiama polinomio caratteristico il polinomio
$$
p(\lambda) = a\lambda^{2}+b\lambda+c
$$
per $\lambda\in \mathbb C$ e equazione caratteristica 
$$
p(\lambda) = 0
$$
### Integrale generale

Data l'equazione caratteristica associata ad una EDO del secondo ordine lineare, omogenea e a coefficienti costanti ho che:
- Se $\Delta>0$ allora esistono $\lambda_{1}\neq\lambda_{2}$ radici del polinomio caratteristico e 
 $$
y_{\sigma}(t) = c_{1}e^{\lambda_{1}t} + c_{2}e^{\lambda_{2}t}
$$
- Se $\Delta=0$ le soluzioni del polinomio caratteristico hanno molteplicità algebrica 2 e quindi
$$
y_{\sigma} (t) = e^{\lambda(t)}(c_{1}+c_{2}t)
$$
- Se $\Delta<0$ allora le radici del polinomio saranno complesse coniugate quindi nella forma $\lambda_{1}=\alpha+i\beta$ e $\lambda_{2}=\alpha-i\beta$
 $$
y_{\sigma}(t) = e^{\alpha(t)}(c_{1}\cos{(\beta t)} + c_{2} \sin(\beta t))
$$

### EDO del secondo ordine lineari non omogenee

Dal teorema di struttura sappiamo che l'integrale generale dell'equazione completa 
$$
a(t)y''(t)+b(t)y'(t)+c(t)y(t)=f(t)
$$
è
$$
y(t) = t_{\sigma}(t) + y_{\phi}(t)
$$
Dopo aver trovato $y_{\sigma}$ dell'equazione omogenea associata si ha che $y_{\phi}(t)$ è una soluzione particolare. 
Ho tre casi semplici per determinare $f(t)$:

1) $f(t)$ è esponenziale quindi $f(t)=Ae^{\gamma t}$
	1) Se $p(\gamma)\neq 0$ allora si cerca $y_{\phi}(t)$ del tipo $y_{\phi}(t) = c e^{\gamma t}$
	2) Se $p(\gamma)= 0$ con $\gamma$ radice singola di $p$ allora si cerca $y_{\phi}(t)$ del tipo  $y_{\phi}(t) = c te^{\gamma t}$
	3) Se $p(\gamma)= 0$ con $\gamma$ radice doppia di $p$ allora si cerca $y_{\phi}(t)$ del tipo  $y_{\phi}(t) = c t^{2}e^{\gamma t}$

2) $f(t)$ è polinomiale quindi $f(t)=q_{n}t^{n}+q_{n-1}t^{n-1}+\dots+q_{0}$
	1) Se $p(0)\neq 0$ allora la soluzione è del tipo $y_{\phi}(t) = \beta_{n}t^{n}+\dots+\beta_{0}$
	2) Se $p(0)= 0$ e $0$ è radice singola allora la soluzione è del tipo $y_{\phi}(t) =t( \beta_{n}t^{n}+\dots+\beta_{0})$
	3) Se $p(0)= 0$ e $0$ è radice doppia allora la soluzione è del tipo $y_{\phi}(t) =t^{2}( \beta_{n}t^{n}+\dots+\beta_{0})$

3) $f(t)$ è trigonometrica quindi $f(t)=A\cos(\eta t)+B\sin(\eta t)$
	1) Se $p(i\eta)\neq 0$ allora $p_{\phi}(t)=c_{1}\sin(\eta t)+c_{2}\cos(\eta t)$
	2)  Se $p(i\eta)=0$ allora $p_{\phi}(t)=t[c_{1}\sin(\eta t)+c_{2}\cos(\eta t)]$
