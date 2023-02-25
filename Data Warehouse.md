Dalla necessità di accedere a dati aggregati in tempo reale
e di eseguire interrogazioni complesse, come l’analisi della correlazione tra diverse variabili, nascono i Data Warehouse. Ovvero delle basi di dati in grado di di estrarre informazioni sia da fonti interne che da fonti esterne.
Tali strumenti rientrano all’interno della cosiddetta [[Business Intelligence]] 

Uno strumento in grado di supportare le attività ai livelli più alti della [[Piramide di Anthony]] è una base di dati che ha caratteristiche diverse da quelle delle classiche basi di dati operazionali:
	• La base di dati può comprendere dati esterni/interni.
	• I dati devono essere organizzati secondo una struttura che faciliti le analisi.
	• La struttura della base di dati deve essere semplice e mettere in relazione tutti e solo i dati di interesse.
	• Le fonti di dati devono essere integrate e aggiornate.
	• Devono essere disponibili strumenti di analisi caratterizzati da brevi tempi di risposta.
	• Deve considerare le principali entità di analisi (ordini, ...)
	• l data warehouse memorizza dati storici
	• I dati non vengono solitamente modificati

Un data warehouse è un sistema [[1. Introduzione#1.3.1 Sistemi OLTP e OLAP|OLAP]] che li distingue dai DBMS [[1. Introduzione#1.3.1 Sistemi OLTP e OLAP|OLTP]] nelle seguenti caratteristiche: 
	• Obiettivo -> i dati devono essere utilizzati per prendere decisioni sugli sviluppi futuri
	• Utenti -> gli utilizzatori dei dati sono i manager di alto e basso livello
	• Orizzonte temporale ->i dati analitici utilizzano dati storici relazionandoli ai dati attuali per identificare problematiche, tendenze e periodicità.
	• Livello di dettaglio -> i dati analitici sono solitamente dati aggregati
	• Accesso -> gli utenti dei dati analitici accedono all’informazione solo in lettura

Oltretutto gode anche delle proprità #FASMI (Fast, Analytical, Shared, Multidimensional, Informational)

## Ipercubo

Il cubo è un oggetto della base di dati il cui valore è definito dalle coordinate rappresentate dalle dimensioni di analisi.
Queste dimensioni sono:
	• Fatti -> è l'elemento ottenuto
	• Misure -> valore numerico del fatto
	• Dimensioni -> coordinate che sono le dimensioni di analisi 

![[Cubo.png]]

## Architettura

All’interno del data warehouse è possibile individuare diverse basi di dati organizzate in modo gerarchico:
	1. Sorgenti -> fonti dei dati 
	2. [[ETL]] -> estrattori di dati dalle sorgenti
	3. Staging Area -> dove sono salvati i dati
	4. Strumenti di analisi

Questi dati possono anche contenere dei [[Metadati]]

![[DW.png]]

## Operazioni

Il #drill_down è l’operazione che permette di ottenere dati più dettagliati scendendo lungo una gerarchia di una dimensione e quindi passando da un livello di aggregazione più alto ad uno più basso.

Il #roll_up in cui il livello di dettaglio si riduce passando ad un livello di granularità inferiore lungo una dimensione di analisi.