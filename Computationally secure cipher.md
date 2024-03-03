---
tags:
  - security
---
To build a computationally secure cipher means to build a cipher so that a successful attack is also able to solve hard computational problems ([[NP-complete]]) efficiently.

The outline of how to create this type of cipher goes like this:
- define the ideal attacker behavior
- assume a given computational problem is hard
- prove that an attacker has to solve the hard problem

If in the algorithm we need some randomness then we have to use a [[Cryptographically safe pseudonumber generator]]. The simplest way to encrypt plaintext would be to use a [[Cryptographically safe pseudonumber generator#Pseudorandom permutation]] for each chunk of the text and put together all the results.

![[PRP enc1.png]]

However this is not secure, this is because $\text{Enc}$ is a deterministic function, and as such if two parts of the plaintext are the same, the resulting output would be the same. This is happens a lot with images for example. To solve this issue we need a way to provide the $\text{Enc}$ with always a **different** input, and the first and easiest way to do this is to just use a counter and then xor the result.

![[CTR.png]]

This is still not secure because to find how the cipher encrypts the text we just need to send a text of all $0$ and all $1$ and see the differences. The fix is quite simple, just start the counter from a random point and then send it in plaintext. 
### Non deterministic encryption

Now to increase the difficult we have an attacker that just wants to understand **which** plaintext gets encrypted and already knows a set of plaintext that can be encrypted. To protect against this we need a non deterministic encryption scheme. This works by:
- rekeying $\to$ change the key for each block
- randomize encryption $\to$ add removable randomness
- use [[NONCE]] 

![[ratcheting.png]]
