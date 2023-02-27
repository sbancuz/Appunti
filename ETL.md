---
tags: [sistemi_informativi]
---
Questi permettono di estrarre, trasformare e caricare i dati del data warehouse.

## Estrazione

L'estrazione dei dati può essere:
	• Statica -> full
	• Incrementale -> delta

## Transformation

A seguito dall’estrazione, i dati necessitano di alcune trasformazioni in quanto derivando da fonti eterogenee possono essere rappresentati in formati diversi e di conseguenza potrebbero risultare non facilmente integrabili, questo passaggio avviene in 3 parti:
	• Pulizia dei dati -> correzione di errori
	• Riconciliazione -> mettere in relazione i dati relativi allo stesso oggetto
	• Standardizzazione dei formati -> i dati sono resi omogeneei
	• Eliminazione dei duplicati

## Loading

Si occupa di caricare i dati nel [[Data Warehouse]]