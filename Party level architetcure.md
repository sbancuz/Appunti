---
tags: [sistemi_informativi]
---
L’architettura Party-level di un sistema di e-business di un partecipante in uno scenario definisce la struttura di quel sistema a livello intra-organizzativo di quel partecipante in termini di: 
	• componenti funzionali software che supportano funzioni specifiche di quel partecipante 
	• interfacce di alto livello che supportano le interazioni fra quei componenti

In un’architettura Party-level, diamo più dettagli che nel [[Market level architecture]] tramite i seguenti raffinamenti:
	• Dettaglio dei sistemi di back end
	• Interfacce tra sistemi back end.
	• Dettaglio delle interfacce tra sistemi front end e back end.

I compponenti delle architetture Party-level sono:
	• Componenti generici -> i principali componenti funzionali.
	• #Database e #DBMS -> denotano componenti per la memorizzazione di dati e i componenti necessari per l’accesso ad essi.
	• Connettori -> entità di collegamento fra i componenti. 
	
Nell’architettura Party-level, mostriamo gli stessi sistemi front-end dell’architettura Market-level e gli altri partecipanti vengono viste come entità esterne.

![[Party level.png]]

Un’architettura funzionale rappresenta i componenti funzionali relativi a uno
scenario cui un’organizzazione partecipa. 
Tuttavia, un’organizzazione può essere coinvolta in scenari multipli, pertanto il party level è un sottoinsieme dell'[[Enterprise Architecture]]

![[PL vs EA.png]]