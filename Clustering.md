Il permette di raggruppare un insieme di elementi in base alle loro caratteristiche, assegnando loro una classe di appartenenza.
l risultato quindi è un insieme di cluster composti da elementi tali che siano verificate le
seguenti condizioni: 
	• la somiglianza tra gli elementi appartenenti allo stesso cluster è massima 
	• la somiglianza tra elementi di cluster diversi è minima.

Per permettere di calcolare la distanza tra gli elementi di un insieme, gli attributi che descrivono gli elementi devono essere numerici.

I principali requisiti con cui gli algoritmi di clustering sono valutati sono:
	• #flessibilità -> capacità di analizzare elementi categorici oltre che numerici 
	• #robustezza -> stabilità del risultato in presenza di rumore
	• #efficienza -> il tempo necessario per ottenere la suddivisione del dataset in cluster
	
Il più diffuso algoritmo di clustering è l’algoritmo #k-means 

![[K-means.png]]

Gli algoritmi di clustering si classificano sulla base dell’assegnazione degli elementi ai cluster. In particolare un algoritmo è:
	• #esclusivo ->  assegna ogni elemento del dataset ad un solo cluster
	• #sovrapposto -> uno stesso elemento può essere assegnato a più classi. 

I metodi di tipo #fuzzy sono metodi sovrapposti in cui l’assegnazione di un elemento ad ogni classe è associata ad un peso che varia tra 0 e 1. 
I metodi si classificano inoltre in #completi se ogni elemento appartiene ad almeno una classe e #parziali se alcuni elementi possono non essere assegnati a nessuna classe.