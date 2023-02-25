La classificazione permette di assegnare in modo automatico gli elementi della
base di dati a classi predefinite. 

La classificazione è una procedura guidata:
	1. Si costruisce un modello in grado di identificare una classe per un elemento #training_set
	2. Si testa il modello con dei dati con classe nota #test_set

Una volta ottenuto un modello soddisfacente è possibile usarlo su dati non classificati per effettuare una predizione sulla classe di appartenenza.
Esistono diversi tipi di classificatori basati su diverse tecniche tra cui funzioni matematiche, reti Bayesiane, [[alberi di decisione]] e reti neurali che differiscono per:
	• Accuratezza -> percentuale elementi classificati correttamente
	• Velocità -> tempo di costruzione delmodello e tempo di classificazione
	• Scalabilità -> capacità del classificatore di costruire un modello con un crescente numero di variabili
	• Robustezza -> capacità di classificazione in caso di elementi mancanti;
	• Interpretabilità -> facilità nell’interpretare i risultati del modello

