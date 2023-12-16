---
tags: [sistemi_informativi]
---
Insieme di elaboratori che condividono il carico lavorativo, applicazioni e dati.
Le server farm sono realizzate secondo 2 principi:
	• [[Cloning]] -> stesse app e dati su più nodi, con servizi di load-balancing
	• [[HW Partitioning]] ->  duplicazione hardware, ripartizione carico

Per risolvere i problemi di entrambe le soluzioni si usano entrambe simultaneamente RAPS (Reliable Array of Partitioned Service)

![[RAPS.png]]

