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