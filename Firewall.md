---
tags: [sistemi_informativi]
---
Il firewall è un insieme di componenti e di servizi finalizzati a controllare e limitare il traffico fra una rete e l'esterno.
I firewall rappresentano la prima linea di difesa per la sicurezza della rete.
Costituiscono una barriera tra le reti interne (Intranet e/o Extranet)

L'adozione di un firewall deve seguire 3 regole:
	• deve essere unico punto di contatto verso l'esterno
	• tutti i pacchetti devono essere bloccati tranne quelli autorizzati
	• deve essere sicuro 

Si possono identificare 2 tipi di firewall rispetto al monitoraggio dei pacchetti:
	• Packet filtering -> blocca o instrada i pacchetti tra le 2 reti, esso guarda l'header del pacchetto (packet_filtering) o del loro intero contenuto (packet_inspection)  
	• Application gateway -> fa da [[Proxy Server]] tra intranet e application server

![[firewall.png]]
![[gateway.png]]

La zona che si trova tra il firewall che riceve il traffico dall'esterno e quella a valle del web server si chiama [[DMZ]]