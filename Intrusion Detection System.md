---
tags: [sistemi_informativi]
---
l'IDS è il processo di monitoraggio degli eventi di un sistema o di una rete, con lo scopo di trovare intrusioni guardando i file log.
Gli IDS possono anche lavorare con i [[Firewall]] per bloccare certe connessioni.

Gli IDS si basano su:
	• attività osservabili
	• le attività normali e anomale sono diverse
	• si usano Features e Modelli
	• processori per audit di dati
	• base di conoscenza
	• un decision engine

![[IDS.png]]

Le componenti funzionali di un IDS sono:
	• Sensori che raccolgono elementi di log
	• Algoritmi di analisi
	• Componenti di Alert and Response

Un’altra classificazione degli IDS avviene in base al tipo di analisi:
	• misuse detection -> individuare i comportamenti già conosciuti noti come attacchi confrontandoli con dei pattern signature
	• anomaly detection -> identifica comportamenti anomali negli host o nella rete.

Infine in base alla risposta che l'IDS da quando rileva un attacco si hanno:
	• Active response -> Acquisisce più informazioni o blocca l'attacco alterando l'ambiente
	• Inactive response -> Invia una notifica all'admin della rete

