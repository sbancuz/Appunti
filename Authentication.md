---
tags:
  - security
---
Authentication deals with the problem of verifying that an entity is actually who it claims to be.

![[authent.png]]

>[!note]
>We use entity because non only a human could have to prove it's identity, even a machine could have to be identified, and subsequently proven to be who it claims

To prove authentication an entity is divided in three factors:
- something to **know** like a password
- something to **have** like a token or a key
- something to **be** like fingerprints
### To know

A password is just a string of bytes, or more commonly text. It's widely spread since it's low cost, easy to use and not *techy* enough to be unusable to anyone. The problem with password doesn't rely in passwords themselves since they should have no meaning. The problem relies on the users of passwords, in fact the most common attack vector is just to steal it or guess it through some sort of [[Social engineering]] attempt and/or [[Shannon information theory]]. More rarely we can just crack a password.

The countermeasures of the third and the second is just to use a better password (duhh) with richer character sets and without data related to the user and to change it often. Too bad we are dealing with humans who are inherently lazy.

The other problem is quite more troublesome to crack, how can we prevent snooping? This is where [[Cryptography]] comes into play!

>[!warning]
>Never store passwords or any kind of secret in plain text
### To have

This can be a physical key or something else that an entity must have. It's relatively low cost and since most likely are limited or even unique, they offer a good level of security. Too bad they can be easily lost, or worse get stolen. This is the precise reason why this method shouldn't be used alone.

A *new* alternative to this is the one time passwords.
### To be

This is the most secure measure of security that we have for humans, for obvious reason. In fact biometrics are quite hard to fake. 