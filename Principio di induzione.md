I numeri naturali soddisfano l'assioma di [[Buon ordinamento]].

Sia P una proprietà dipendente da un naturale n, scrivo P(n) per dire che "n ha la proprietà P" dove P può essere vero o falso.

Se:
	1 • vale P(0)
	2 • se vale P(n), allora vale anche P(n + 1)

Allora P(n) è vera per ogni naturale $n\ge 0$

>[!note]- Dimostrazione
Sia S l'insieme così definito $$S=\{n \in N \text{ | } P(n) \text{ è falsa}\}$$
Allora provo che $S = \emptyset$ 
Supponiamo per assurdo che $S \not= \emptyset$ allora per l'assioma dell'ordinamento S ha un minimo m.
Per definizione di S, P(m) è falsa di conseguenza $m \not= 0$ allora $m- 1  \in N$ e dunque $m-1\notin S$
(altrimenti m non sarebbe il minimo) e quidni P(m - 1) è vera, ma allora per ipotesi si ha che P(m) è vera che è un assurdo.

>[!Tip] Esempio
>Provare che $7^n - 3^n$ è multiplo di 4
>Provo per induzione
>	1 • $P(0) \text{è vera} = 1 - 1 = 0$ che è multiplo di 4
>	2 • Supponiamo che n sia tale che $7^n - 3^n$ è multiplo di 4, vediamo se è vera
>			$7^{n+1} - 3^{n+1} = 7*7^n - 3*3^n = (4+3)*7^n - 3*3^n = 4*7^n + 3*(7^n - 3^n)$
>		
>	$(7^n - 3^n)$ per ipotesi induttiva è multiplo di 4 e allora P(n) è valida

>[!warning]
>
Il principio di induzione è uno strumento dimostrativo non di scoperta



