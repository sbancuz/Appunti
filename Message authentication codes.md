---
tags:
  - security
---
### Malleability

Another problem with ciphers is when the attacker, without knowing the key, makes changes to the data that correspond to a predictable behavior in the plaintext. To protect from this we need to add **data integrity**.

>[!info]
>Being malleable can be a **feature**, and we call this ciphers **homomorphic** 
### MAC

This is a small piece of information that allows us to test for the message integrity of the encrypted message.

>[!warning]
>They do not provide data authentication

They are constituted by a pair of functions
- $\text{Compute tag}(str, key)$ $\to$ that returns the tag
- $\text{Verify}(str,tag,key)$ $\to$ that return `true` or `false`

To create the compute tag function we can try with a [[Computationally secure cipher#Non deterministic encryption]]

![[CBC-MAC.png]]