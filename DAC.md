---
tags: [sistemi_informativi]
---
Le regole di accesso possono essere specificate nel profilo utente, oppure associate alla descrizione dell’oggetto. I meccanismi base per la specifica di autorizzazioni possono essere inseriti nel Query Language del DBMS o nei comandi di SO.

**Grant** -> concedere permessi

Adesso si ha un modello a 6 componenti per DAC:
	(grantor, grantee, obj, right, constraint, prop_rule)
Con prop_rue che specifica come i privilegi si propagano:
	• No propagation
	• Bounded propagation
	• Unbounded propagation

![[DAC.png]]
![[DAC2.png]]

