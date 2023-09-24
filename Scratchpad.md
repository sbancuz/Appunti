Dare definizione di differenziabilità:

Sia $A\subseteq \mathbb{R}^{2}$ aperto e sia $f:A\to \mathbb{R}$  allora diciamo che $f$ è differenziabile se definiamo la funzione resto
$$
R(\underline{h}) = f(\underline{x}_{0} + \underline{h}) - f(\underline{x}_{0}) - \left< \triangledown f(\underline{x}_{0}), \underline{h} \right>  
$$
e quindi 
$$
f(\underline{x}) = f(\underline{x}_{0}) + \left< \triangledown f(\underline{x}_{0}), \underline{h} \right> + \sigma(||\underline{x} - \underline{x}_{0}||)
$$


Dimostrare la continuità data la differenziabilità

Data la definizione di differenziabilità:
$$
f(\underline{x})  = f(\underline{x}_{0}) + \left< \triangledown f(\underline{x}_{0}), \underline{h} \right> + \sigma(||\underline{x} - \underline{x}_{0}||) 
$$
devo dimostrare che 
$$
\lim_{ x \to x_{0} } {f(\underline{x}_{0}}) = f(\underline{x}) 
$$

dalla diseguaglianza triangolare e di Cauchy-Schwarz si ha che
$$
0 \leq ||f(\underline{x}) - \underline{f}(\underline{x}_{0}) || \leq ||\triangledown f(\underline{x}_{0})|| ||\underline{h}|| + \sigma(||\underline{x}-\underline{x}_{0}||)
$$
che prendendo il limite per $\underline{x} \to \underline{x}_{0}$ si ha che 
$$
0 \leq ||f(\underline{x}) - f(\underline{x}_{0})|| =0 + 0 = 0
$$
e quindi la condizione è verificata.


---


Dire cosa si intende per equilibrio stabile di un equazione differenziale autonoma del primo ordine ed enunciare il relativo criterio di stabilità.


Per equilibrio stabile di una EDO del primo ordine autonoma si intende un punto per il quale la funzione tende localmente e, anche se perturbata tende sempre a quel punto di equilibrio, quindi


---

Dare la definizione di convergenza puntuale e totale delle funzioni. Dare esempi di funzioni che convergono puntualmente, ma non totalmente.


Una funzione converge puntualmente in un intervallo $I$ se per ogni punto $x\in I$ la successione numerica converge.
Se inoltre la funzione converge puntualmente in tutto $\mathbb{R}$ e la somma $\sum sup|f(x)|$ converge

---

lunghezza di una curva

Sia $r(t)$ una curva regolare in $\mathbb{R}^{n}$ definita con sostegno $\gamma$ su un intervallo $I$ allora la sua lunghezza sarà
$$
\int _{I}||r'(t)|| \, dx 
$$

Per dimostrare che la lunghezza è invariante per una riparametrizzazione di una curva con sostegno $\gamma$ prendo $\phi$ il cambiamento di variabile definito su $[c,d]\to[a,b]$ e $\underline{v}(s)$ come $v(\phi(t))$

Sia ha che $\underline{v}' = (v(\phi(t)))'$ che per la regola di derivazione delle funzioni composte sarà $=\underline{v}'(\phi(t))\phi'(t)$ oltretutto col cambio di variabile $t = \phi(s)$ $dt = \phi'(s)ds$.
Quindi la riparametrizzazione ha due casi: 
- se $f$ è crescente allora $a<b \implies \phi(c)<\phi(d)$ quindi
$$
\int _{a}^{b} r'(t)\, dt = \int _{c}^{d} (v(\phi(t)))' \, dt = \int _{c}^{d} v'(s)\, ds   
$$

...

---

Sia $A\subseteq \mathbb{R}^{2}$ e sia $f:A\to \mathbb{R}$.  Se esiste $\delta>0$ tale che per ogni $x_{0}\in A$ $\forall {\epsilon}> 0 {}$ $|f(x)-l|<\epsilon$ e$x\in B_{\delta}\setminus \{ x_{0} \}$
$$
\lim_{ (x,y) \to (x_{0},y_{0}) } {f(x)} = l
$$

---

$$
\begin{align}
y_{s}  =  & \begin{cases}
1  & x_{s} > 0 \\
0  & otherwise
\end{cases} \\
y_{a}  =  & \begin{cases}
1  & x_{s} \geq a \\
0  & otherwise
\end{cases} \\
y_{b}  =  & \begin{cases}
1  & x_{s} \leq b \\
0  & otherwise
\end{cases} \\
 & \begin{cases} 
z = y_{a} \times y_{b} \\
z + (1 - y_{s}) - s_{l} \geq 1  & \text{ xor }\\ 
x_{s} \leq My_{a} \\
\end{cases}
\end{align}
$$