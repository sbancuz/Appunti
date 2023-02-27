---
tags: [sistemi_informativi]
---
La crittografia asimmetrica richiede che ogni agente sia in possesso di una coppia di chiavi correlate: 
	• una chiave pubblica KP 
	• una chiave privata Kpr
Tutto ciò che è cifrato con la chiave privato è decifrabile solo con quella pubblica e viceversa.

Le Kpr non sono mai condivise, invece le KP sono sempre disponibili su repository pubblici.

![[Asimmetrica.png]]

L'algoritmo più famoso è l' #RSA che si basa sul trovare fattori primi di numeri enormi.

## Funzioni di hash

Per garantire anche l'integrità abbiamo bisogno anche di funzioni di hash che trasforma un messaggio in un impronta digitale ed ha le seguenti proprietà:
	• Coerenza
	• Univocità
	• Non invertibilità

![[Hash.png]]

Quest'impronta deve essere utilizzata insieme ai sistemi a chiave pubblica
tramite alla firma digitale

## Firma digitale

Obiettivo della creazione e apposizione a un dato/informazione di una firma digitale è garantire l’autenticità dei dati e identificare con certezza il loro creatore.
La firma digitale è definita come il digest di un documento che poi viene crittografato, che poi viene spedita insieme al messaggio.

![[firma digitale.png]]

## Aspetti di gestione delle chiavi e certificati digitali

La generazione delle chiavi è fatta firettamente da chi effetuerà le operazioni crittografiche e devono essre stringhe causali di bit.

Le chiavi private sono salvate solo sul computer che le genera.
Le chiavi pubbliche vengono diffuse tramite un certificato dalle #PKI che sono infrastrutture che:
	• emettono certificati
	• revocano certificati
	• distribuiscono certificati
	• validazione firme digitali

![[PKI.png]]

Per garantire che il certificato non possa essere alterato, esso viene protetto con la firma digitale dell’Autorità di Certificazione che lo ha emesso. Quando si riceve una chiave pubblica attraverso un ceritficato occorre controllare l'integrità e validità della firma.

Ora c'è solo da vedere se la CA che ha emesso il certificato sia fidata tramite la RA.
