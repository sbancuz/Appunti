Per essere un sottomonoide devo verificare che l'elemento neutro faccia parte del monoide $M_{1}$ e che sia chiuso nell'operazione

Sia $e_{1}$ l'identità di $M_{1}$ e $e_{2}$ quella di $M_{2}$. Per la definizione di morfismo di monoidi ho che $f(e_{1}) = f(e_{2})$. Visto che $Y$ è sottomonoide di $M_{2}$, ho che $e_{2} \in Y$. Quindi si ha che $f^{-1}(e_{2}) = e_{1}$ che fa parte di $M_{1}$.

Siano $a,b\in f^{-1}(Y)$. Quindi ho che $f(a),f(b) \in Y$ per definizione. Poiché sappiamo che $Y$ è sottomonoide di $M_{2}$, sappiamo che è chiuso rispetto all'operazione di $M_{2}$. Quindi $f(a)f(b)\in Y$ e in quanto morfismo di monoidi $f(ab) = f(a)f(b) \in Y$

---

Per mostrare che $f^{-1}(H)$ è un sottogruppo di $G_{1}$ devo verificare le $3$ proprietà del sottogruppo in $G_{1}$
1) Chiusura per l'operazione
	Siano $a,b\in f^{-1}(H)$, per definizione so che $f(a)f(b)\in H$ che è sottogruppo di $G_{2}$ quindi chiuso per l'operazione associata. In quanto morfismo di gruppi si ha che $f(a)f(b) = f(ab) \in H$. Per definizione di $f^{-1}$ se $f(ab) \in H$ allora $ab \in f^{-1}(H)$ quindi è chiuso

2) Ha l'identità
	Siano $e_{1},e_{2}$ le identità di $G_{1},G_{2}$. Allora si ha che $f(e_{1}) = e_{2} \in H$ per le proprietà di morfismi di gruppi e per il fatto che $H$ è un sottogruppo di $G_{2}$. Per la definizione di $f^{-1}(H)$ si ha che se $f(e_{1})\in H$ allora $e_{1} \in f^{-1}(H)$. Quindi ha l'elemento identità

3) Chiuso per l'inversione
	Sia $a\in f^{-1}(H)$, per definizione si ha che $f(a) \in H$ e $a \in G_{1}.$ Poiché $H$ è un sottogruppo deve contenere l'inverso di ogni elemento. Quindi $(f(a))^{-1}\in H$, quindi $f^{-1}(a)\in H$. Per definizione di $f^{-1}(H)$ se $f^{-1}(a)\in H$ allora $a^{-1} \in f^{-1}(H)$

---

Per il teorema di isomorfismo dobbiamo trovare $\phi: G_{1} \times G_{2} \to (G_{1} / H_{1}) \times (G_{2}, H)$ tale che $\phi$ sia suriettivo e $Ker(\phi)$ sia $H_{1} \times H_{2}$  