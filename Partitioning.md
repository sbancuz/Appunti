La tecnica di partizionamento prevede la duplicazione dell’hardware, per ripartire l’esecuzione dell’applicazione tra i nodi.

Ogni nodo svolge una funzione specializzata, le richieste vengono inviate alla partizione che possiede i dati rilevanti. Questa tecnica però non migliora la disponibilità in quanto tutti i dati sono su un solo server e se ci fosse un guasto avremmo una #gracefull_degradetion, quindi solo certe funzionalità sono inaccessibili

![[Partitions.png]]