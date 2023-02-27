---
tags: [sistemi_informativi]
---
Il paradigma hub and spoke è basato su un hub centrale, a cui vengono collegati i sistemi tramite degli spoke, che fungono anche da adattatori.

Un sistema invia il messaggio all'hub senza dire dove dovrà dirigersi, sarà compito dell'hub instradarlo verso il modulo opportuno.

![[Hub and spoke.png]]

Nell’ architettura di integrazione hub and spoke, la realizzazione dell’integrazione comprende anche la definizione dell’ordine di esecuzione delle operazioni in modo implicito nelle regole. Questo è gestito dal [[BPMS]].