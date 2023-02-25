Si parla di clonazione quando sui server vengono installate le stesse applicazioni software ed i medesimi dati. Le richieste sono poi instradate ai vari elementi appartenenti all’insieme dei cloni usando un sistema di load-balancing.

Un insieme di cloni dedicati allo svolgimento di un particolare servizio è detto
#RACS (Reliable Array of Cloned Services).
La clonazione del servizio permette di ottenere vantaggi sia di scalabilità sia di tolleranza ai guasti #fault_tolerance in termini di disponibilità del servizio.

Ci sono 2 configurazioni per la gestione dei dati:
	• #shared_nothing -> dati duplicati per ogni clone, fs #read_only
	• #shared_disk -> datu condivisi a tutti, utili per #write_intensive app

![[sh nothign.png]]

![[shared.png]]

