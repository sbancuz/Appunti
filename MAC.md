---
tags: [sistemi_informativi]
---
I sistemi gestiti in base a politiche mandatorie sono adatti per database con dati sensibili dove esistono diversi livelli di sensitività, e dove sono necessari anche controlli sul flusso di dati, controlli sul rilascio di dati e controlli sugli utenti.

I meccanismi di sicurezza che implementano politiche MAC devono garantire
che tutti i soggetti abbiano accesso solo ai dati per cui possiedono la clearance
appropriata. Le regole sono base sono:
	1. No-Read-Up -> Un soggetto S è autorizzato ad accedere in lettura a un oggetto O solo se L(S) >= L(O).
	2. No-Write-Down -> un soggetto S è autorizzato ad accedere in scrittura a un oggetto O solo se L(S) <= L(O).

Tipici livelli di classificazione sono:
	• Unclassified (U)
	• Confidential (C)
	• Secret (S)
	• Top Secret (TS).

![[MAC.png]]

Meccanismo fondamentale per la realizzazione è la polinstanziazione, ovvero l’istanziazione multipla di tabelle fisicamente separate a seconda della loro classificazione di sicurezza. Essa avviene tramite delle regole di relazione degli elementi MLR

![[polistanza.png]]