I nodi sono gli attributi del soggetto da classificare 
Gli archi sono i valori assumibili dall’attributo
Le foglie sono le classi a cui gli elementi possono essere assegnati

![[Decision Tree.png]]

La costruzione di un albero di decisione si svolge tramite raffinamenti successivi.

Un albero di decisione risulta quindi perfetto quando è in grado di classificare ogni elemento in una classe identica a quella per cui è stato etichettato.
Tuttavia nella realtà esistono sempre delle discrepanze, e queste sono calcolate partendo dall’analisi dei cosiddetti falsi positivi #FP e falsi negativi #FN. Si possono definire anche i cosiddetti veri positivi #TP e veri negativi #TN che, contrariamente ai casi precedenti, indicano quando correttamente un individuo è inserito, o non inserito, in una classe.

![[Precision e Recall.png]]

A partire da questi valori posso definire:
	• #Precision -> TP / (TP + FP )
	• #Recall ->  TP / (TP + FN )