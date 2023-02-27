---
tags: [sistemi_informativi]
---
### Discutere cosa si intende per sistema di gestione del workflow
--- [[BPMS]]

Per sistema di gestione del workflow si intende una suite di applicazioni che vengono gestite secondo un modello processuale, workflow model, da gruppi di lavoro collaborativi.
Un processo consiste in un insieme di attività che vengono svolte per ottenere un obiettivo comune. Queste attività rappresentano lavori da svolgere e possono essere sia manuali, nel senso che devo essere svolte da un utente, un operatore, o possono essere automatiche.
I sistemi software che sanno interpretare una serie di regole procedurali integrano diverse funzioni: utilizzano strumenti dell'information technology per la condivisione dell'informazione e gestiscono la comunicazione ed il passaggio dei compiti da un collaboratore all'altro. Questi sistemi vengono chiamati Workflow Management Systems e forniscono vari vantaggi:
	- Migliorano l'efficienza -> l'automazione di varie task permette sia l'eliminazione di passi non necessari e permette anche di spostare lavoro da un utente ad un sistema che può essere disponibile 24/7 o che semplicemente è più veloce a svolgerle
	- Migliore controllo del processo -> avere un sistema che gestisce come una determinata attività deve essere svolta porta alla standardizzazione del processo di svolgimento di tale, quindi, essendo standard, si riesce a controllare a che punto sia una determinata attività, se ci sia qualche intoppo o se venga svolta incorrettamente

I Workflow Management System sono dei software applicativi da installare sui computer dei collaboratori, molti vantaggi del workflow management sono dati la mantenimento e l'organizzazione dei contatti, soprattutto quando lo scopo del lavoro è molto ampio e eterogeneo nello spazio.

### Illustrare i modelli per la segmentazione dei sistemi informativi (piramide di Anthony, catena del valore, segmentazione orizzontale e verticale, ...)

-- [[Piramide di anthony]]
La piramide di Anthony descrive la struttura che un organizzazione deve avere, i principali livelli partendo dal basso sono:
	- il livello operativo, detto anche livello operazionale, dove si svolgono la maggior parte delle attività aziendali "comuni", nel senso che avvengono molto spesso
	- il livello di programmazione e controllo, in cui si considerano le attività tattiche quali la programmazione delle risorse e il conseguimento degli obiettivi aziendali prestabiliti
	- il livello di pianificazione strategica in cui si prendono decisioni, fissano obiettivi strategici per il futuro sviluppo dell'organizzazione e si definiscono anche le politiche aziendali

-- [[Catena del valore di Porter]]
La catena del volere di Porter considera i processi a livello operazionale. Secondo questo modello una generica organizzazione viene vista come un insieme di 9 processi, di cui 5 primari orientati sugli obiettivi principali dell'azienda, e 4 di secondari che vengono visti come processi di supporto. Questo modello è molto utilizzato da organizzazioni che producono beni fisici, tuttavia si può usare anche come spunto per l'analisi dei processi.

-- [[1. Introduzione]]
La piramide della conoscenza descrive come i dati si possono vedere e interpretare, se la osserviamo dal basso verso l'alto vediamo che nonostante la piramide si restringe quello che ne possiamo tirare fuori, in senso di informazioni e conoscenza. Alla base della piramide abbiamo i dati, che sono semplicemente delle misure numeriche all'interno di un data warehouse o di un DBMS, da soli non dicono molto però quando si aggregano diventano informazioni, passiamo da prima che abbiamo per esempio delle letture casuali della temperatura di una stanza ad una rappresentazione che ci può dare informazioni sull'andamento temporale della temperatura. Al livello successivo abbiamo la conoscenza che è quando all'informazione integriamo l'esperienza e ciò può guidarci a fare determinate decisioni. Per ultimo livello abbiamo la saggezza che è definita come come l'esperienza applicata alla conoscenza.

### Illustrare il ruolo dei dati in un sistema ERP
-- [[8. ERP]]
Il ruolo dei dati in un sistema ERP è fondamentale, in quanto esso è stato sviluppato apposta per offrire moduli di supporto a livello operazionale all'interno di un azienda. L' ERP è necessario per garantire l'unicità dei dati tra i moduli interni che gestiscono le transazioni aziendali.

### Illustrare le caratteristiche generali dei sistemi ERP. Discutere poi le alternative  per la loro adozione all'interno di un sistema informativo rappresentandole in un diagramma architetturale secondo l’approccio BOAT:
-- [[8. ERP]]
-- [[3. BOAT|BOAT]]
Le principali caratteristiche dei sistemi ERP sono:
1. L'unicità dei dati tra i moduli tutti i moduli interni che gestiscono le varie transizioni aziendali
2. Modularità, la suite software è composta da moduli autosufficienti che possono essere acquistati in modo incrementale e facilmente integrati all'interno di un sistema più complesso. Ogni modulo generalmente compie una serie di funzioni elementari
3. Prescrittività, quindi la certezza che i moduli, i dati ed i processi funzionino all'interno dell'organizzazione secondo quelle che sono le business rules
Secondo l'approccio BOAT l' ERP può essere rappresentato tramite l'architettura party level.

### Introdurre il concetto di data mining. Inoltre, spiegare obiettivi, valutazione e possibili applicazioni degli alberi di decisione.
-- [[9. Data Mining]]
l'interazione con i sistemi di data warehousing permette all'utente di svolgere attività di analisi dei dati in essi presenti con lo scopo di estrarre in modo automatico informazioni da un immensa mole di dati numerici, questo concetto si riporta molto alla piramide della conoscenza, dove si vede che dall'aggregazione dei dati si può ottenere un informazione che è molto più della somma delle parti. Uno di questi meccanismi automatici sono gli alberi di decisione; essi sono degli alberi, possibilmente anche a n figli, che definiscono tramite regole specifiche la classificazione di determinati dati. Gli alberi vengono spesso usati con meccanismi di machine learning soprattutto per basi di dati estremamente grandi e complessi. Questi diagrammi sono fatti con scopi per esempio di marketing: nel vedere potenziali nuovi clienti, per ritenere quelli già esistenti o semplicemente mostrare pubblicità personalizzate.


### Descrivere la scelta make or buy discutendone vantaggi e svantaggi. Illustrare poi il processo di selezione del software e gli indicatori che influenzano la scelta
-- [[Make-or-Buy]]
La scelta make or buy si pone quando si sta progettando un nuovo modulo, un aggiornamento o direttamente un intero sistema informativo all'interno di un enterprise architecture. Il make rappresenta l'implementazione delle funzionalità necessarie con un modulo sviluppato in house, con i vantaggi di essere estremamente integrato nel sistema informativo dell'organizzazione essendo fatto ad hoc per essa e rende anche facile l'aggiornamento e la manutenzione del modulo stesso; tra gli svantaggi però abbiamo che ha bisogno di una grande quantità di risorse monetarie, temporali e umane per il suo sviluppo e molte volte sarà anche difficile da integrare con altri moduli comprati successivamente in quanto si corre il rischio di non essere conforme con vari standard sul mercato. In contrapposizione abbiamo le soluzioni di tipo buy, dove un organizzazione compra un applicativo standard già sviluppato e applica piccole modifiche per integrarlo nel sistema informativo già esistente, con il vantaggio di essere un processo molto rapido e poco costoso, con questo però ne va dell'integrazione "perfetta" con le esigenze del settore.
Gli indicatori che influenzano la scelta sono: il tempo, il costo di creazione e di manutenzione ( che in caso di un azienda non IT può essere molto alto in quanto dovrà farlo fare delle aziende che lavorano a contratto per gestirlo )

### Illustrare il procedimento di firma digitale e verifica della firma
-- [[13. Sicurezza dei sistemi]]
Ci si riferisce alla firma digitale quando si parla del digest di un messaggio o di un file, quindi il risultato di quello stesso messaggio passato tramite un a funzione di HASH (tipicamente la SHA256), questo digest poi viene crittografato utilizzando la chiave privata del mittente. Questa tecnica infatti viene utilizzata con lo stile di crittografia asimmetrica a due chiavi attraverso algoritmi tipo l'RSA. Per verificare che una firma sia autentica si deve interrogare una CA (certification authority) per convalidare la chiave pubblica del mittente e, se valida, usarla per decriptare il digest, a questo punto si applica di nuovo la funzione di hash sul messaggio che è arrivato e si confronta con il digest decriptato. A loro volta le CA sono validate dalle RA (Registration Authority).

### Rappresentare e descrivere l’architettura del data warehouse soffermandosi in particolare sul modulo ETL
-- [[Data Warehouse]]
Una data warehouse una base di dati che differisce dai tradizionali DBMS in quanto i suoi dati sono storici, read-only, contiene dati da sorgenti sia interne che esterne, sono organizzati in modo tale da facilitare le analisi e le aggregazioni. Questo appunto è un sistema OLAP. I componenti base di un data warehouse sono i cubi, ovvero delle "coordinate" nella base di dati che descrivono una particolare informazione, questi cubi sono composti da 3 tipo di informazioni: l'etichetta dell'elemento, quindi il cosa rappresenta, un orizzonte temporale (quando è stato preso, per quanto è valido, ...) e infine un indicatore numerico che lo quantifica. Il modulo ETL rappresenta un componente che:
	- Estrae le informazioni tra le varie sorgenti di dati esterne e/o interne
	- Trasforma queste informazioni cosi da eliminare dati sbagliati, eliminare duplicati, pulire e conformare il dato e infine creare delle connessioni con i dati già presenti al suo interno
	- Caricamento dei dati (Loading) e quindi il loro salvataggio nella data warehouse


### Descrivere le funzionalità dei moduli del CRM e in che modo questi moduli interagiscono
-- [[CRM]]
-- [[IA]]
Il CRM è una suite di software che supporta le organizzazioni nelle interazioni con i clienti, ponendo al centro della strategia aziendale il cliente.
Il CRM si divide in:
	- Operativo che si occupa dell'interazione coi clienti attraverso attività di marketing
	- Collaborativo che si occupa di calcolare indici rilevanti per l'azienda, questi indici possono essere la profittabilità o la soddisfazione dei clienti
	- Analitico che si occupa di registrare le interazioni col cliente in un unica base di dati, che poi verranno usati per estrarre pattern significativi dai clienti attraverso anche tecniche di machine learning

### Descrivere le principali tipologie di attacco a livello di rete, indicando quali proprietà della sicurezza violano
-- [[13. Sicurezza dei sistemi#13.1 Minacce, violazioni, vulnerabilità, attacchi]]
Gli attacchi a livello di rete sono 4:
	- Sniffing che consiste nel intercettazione dei messaggi quindi violando la riservatezza
	- Spoofing ovvero impersonare un mittente per scopi malevoli, violando l'autenticità
	- Man in the middle si ha quando si combina sia sniffing che spoofing, violando quindi riservatezza e autenticità
	- Flooding, quindi l'atto di congestionare la rete della vittima rendendo il servizio offerto non più disponibile per i clienti, quest'ultimo viola la disponibilità


### Descrivere le principali tipologie di algoritmi di data mining. Descrivere poi in dettaglio le regole associative e la loro valutazione

Esistono vari tipi di algoritmi di data mining, i 2 più rilevanti sono:
	- Classificazione -> procedura guidata che permette di assegnare classi a dei dati
	- Clustering -> raggruppa elementi simili tramite un insieme di caratteristiche tentando di rispettare al più possible 2 regole: la somiglianza degli elementi in un cluster è massima e gli elementi di cluster diversi hanno una somiglianza minima

Le regole associative sono delle relazioni tra 2 classi di dati che vengono spesso espresse con l'implicazione logica A => B e vengono valutate in base al:
	- supporto -> percentuale di eventi che soddisfano l'antecedente rispetto al totale
	- confidenza -> inferenza baysiana P(B|A) = P(A,B) / P(B)


### Illustrare la piramide di Anthony

La piramide di Anthony è un modello gerarchico che descrive i livelli di un organizzazione:
in cima si ha il livello strategico che prende decisioni sul futuro dell'organizzazione, definisce strategie di business e le varie politiche aziendali.
in mezzo si trova il livello tattico che si occupa di implementare le strategie definite al livello superiore e trasmetterle a livello operativo.
Infine c'è il livello operativo che è quello che svolge le funzioni dell'azienda.

I processi possono comunicare con dei flussi informativi che possono attraversare il livello in cui sono stati generati, ma anche passare da un livello all'altro nel caso lo si necessiti.

### Opportunità SaaS per le aziende: Vantaggi vs Svantaggi

SaaS sta per software as a service, quindi quando paghi per utilizzare un software presente su un host remoto condiviso da molti altri utenti
I vantaggi sono:
	- Costo -> visto che non bisogna sviluppare quasi nessuna infrastruttura implementare questi servizi i costi si guardano solo in termini di utilizzo del web server in questione
	- Supporto -> il software in questione è gestito da un'altra entità esperta sia in termini di sicurezza (visto che vendono un servizio software) sia in termini di supporto features

Gli svantaggi sono:
	- Sicurezza -> nonostante sotto certi aspetti la sicurezza sia un punto forte, il fatto di gestire SaaS per molte aziende rende questi servizi delle ottime prede per potenziali attacchi
	- Località dei dati -> non si può sapere dove geograficamente le informazioni siano salvate, questo può essere critico per informazioni sensibili in quanto ci sono leggi che dettano dove certe informazioni possano essere salvate
	- Disponibilità del servizio -> il servizio necessita sempre di internet

### Secondo l’approccio BOAT, discutere le differenze tra la progettazione degli aspetti relativi all’organizzazione e quelli relativi alle architetture, e discutere in particolare la rappresentazione dell’interazione tra le parti

La progettazione di un sistema informativo comprende sempre attività di natura molto diverse che spaziano tra decisioni di business a implementazioni tecnologiche. Al fine di svolgere questa dividiamo la progettazione in 4 macro-aree che corrispondono ai 4 aspetti di BOAT:
	- Business -> bisogna valutare bene gli obiettivi di business
	- Organisation -> si descrive come l'organizzazione deve essere strutturata per riuscire a coprire quegli obiettivi definiti precedentemente. Gli aspetti principali trattati sono i processi definiti con le aziende esterne e la definizione dei front end systems
	- Architecture -> descrive come nel back end la soluzione di business viene realizzata, che sia attraverso CRM, ERP, HR o vari DB
	- Technology -> infine dobbiamo dire come effettivamente devono essere implementate a livello fisico e/o virtuale (nel caso si usino macchine virtuali) le tecnologie, quindi si dovrà definire l'infrastruttura a partire da come il cliente interagisce con i servizi a come essi vengano eseguiti su uno o più server

### Illustrare il modello di Porter e discutere le relazioni con gli aspetti di modellazione organizzativa di un sistema informativo

Il modello della catena del valore di porter descrive un organizzazione come un insieme limitato di processi. Infatti si identificano 9 processi di cui 5 primari che si occupano delle funzioni principali dell'organizzazione e i restanti 4 sono di supporto ad essi. Questo modello si adatta bene alle organizzazioni che producono beni/servizi, ma non alle medie/piccole imprese. Nel caso di un e-business questo modello manca di front end e back end nei processi primari.

### Illustrare il ruolo delle architetture funzionali nella progettazione

Le architetture funzionali definiscono come implementare le necessarie funzioni di business sotto 3 livelli:
	- livello di mercato che si interfaccia con il mercato identificando tutti gli attori che faranno parte della transazione di business
	- party level che descrive le strutture a livello di organizzazioni singole descrivendo le interfacce di front-end e in maniera dettagliata la backend 
	- system level che descrive le strutture dei sottosistemi di un partecipante di e-business, ovviamente questo livello si concentra sulla intra-organizzazione e possiamo trovare soluzioni COTS 

### Illustrare le motivazioni dell’integrazione delle applicazioni di un sistema informativo. Descrivere come si possono integrare applicazioni nell’ambito di una architettura a servizi

Il motivo per integrare delle applicazioni in un sistema informativo è quello di permettere la comunicazione tra esse, la condivisione dei dati, l'integrazione di nuove funzionalità senza dover spendere troppe risorse. Un buon esempio di ciò sono le architetture hub and spoke dove bisogna solo creare un interfaccia dall'applicazione in questione verso l'hub e creare dei processi che ne supportano l'utilizzo. Altro esempio sarebbe l'adozione di Enterprise Bus System.
L'architettura a servizi prevede che ogni modulo del sistema informativo deve implementare solo un servizio e un interfaccia per interagire con esso, queste interfacce possono essere delle RESTfull API che permettono di richiedere informazioni da un server con una richiesta HTTP attraverso un URI.

### Discutere le possibili configurazioni dei livelli logici (layer) in architetture a tre tier

I 3 tier sono:
	- Presentazione -> questo rappresenta la GUI con cui l'utente che usufruisce di questo servizio deve interfacciarsi, questo può essere rappresentato con una web app che viene posta su un web server e poi esposta all'internet o anche come un app per telefono che invierà richieste al  livello di applicazione
	- Applicazione -> qui viene rappresentata tutta la logica, tutti i flussi di dati ed i processi che servono per far funzionare l'applicazione in questione. I dati non risiedono su questo livello, ma semplicemente vengono fatte richieste ai nodi su cui risiedono
	- Dati -> qui risiedono tutti i dati in DB standard o DW

Ci sono varie configurazioni disponibili per sviluppare un applicazione:
	- thin client -> il client possiede lo il livello di presentazione e tutto il resto è gestito da 2 o più nodi server dipendentemente dal bisogno di più o meno funzionalità
	- thick client -> il cliente ha in se sia la presentazione che la logica per far funzionare l'app, il client si limita a fare richieste tramite delle chiamate API per richiedere i dati che servono per il  funzionamento
	- distributed architecture -> questa categoria rappresenta quelle app il cui livello di applicazione non sta interamente ne sul client, ne sul server, ma su entrambe

### Descrivere la fase di pianificazione nel ciclo di vita dei Sistemi Informativi

Ci sono due approcci allo sviluppo di un sistema informativo:
	- make -> ovvero lo sviluppo in house del modulo applicativo, esso è diviso in ulteriori fasi:
		- Analisi dei requisiti
		- Sviluppo incrementale degli applicativi
		- Test di funzionalità
		- Integrazione del nuovo modulo nel sistema
		- Manutenzione
	- buy -> comprare modulo COTS che solitamente è già stato provato nel mercato in questione
		- Ricerca di un Vendor
		- Analisi delle funzionalità
		- Incontro coi vendors 
		- Pianifica modifiche del prodotto per l'integrazione
		- Quotazione
		- Acquisto