---
tags: [sistemi_informativi]
---
Il process mining è usato per scoprire, monitorare e migliorare i processi attraverso l'estrazione di conoscenza dai #log

![[Process mining.png]]

Ci sono 2 ingredienti principali:
	• Event data -> per guardare le prestazioni
	• Process Models -> per guardare la compliance

Inoltre si hanno 3 tipi di process mining:
	• Process discovery -> da un event log si produce un modello senza informazioni a-priori
	• Conformance checking -> un modello viene comparato con dei log per vedere se sono conformi tra loro
	• Enhancement -> Migliorare un modello esistente attraverso i logù

## Event LOG

Gli event log registrano informazioni relative all'esecuzione di un [[Processi|processo]].
Gli elementi principali dell'event log sono:
	• CASE_ID
	• ACTIVITY_ID
	• TIMESTAMP -> <start, complete, suspend, resume, abort>
I log sono salvati nel formato #XES che rilevano la traccia del processo

![[traccia.png]]