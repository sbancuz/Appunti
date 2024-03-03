---
tags:
  - security
---
It's the study of the techniques to allow secure communication and data storage in presence of attackers. With cryptography we want to ensure:
- Confidentiality $\to$ data can be accessed only by chosen entities
	There are multiple ways an attacker can accesses unauthorized data: eavesdropping, it knows already a set of plaintexts or, it may tamper with the data trying to decrypt it. To solve there are [[Perfectly secure cipher]] and [[Computationally secure cipher]]
	
- Integrity $\to$ prevent tampering or replays
	To achieve this we either design an intrinsically non tamperable cipher, which is quite the task, or simply add some information using [[Message authentication codes]]
	
- Authenticity $\to$ data and their origin are certified
- Non-repudiation $\to$ creator cannot repudiate data
- Advanced features $\to$ proof of knowledge
### Kerchoff's principles of ciphers
1) It must be **practically** unbreakable
2) It should be possible to make it public
3) The key must be communicable without written notes and changeable
4) Applicable to telegraphic communication
5) It must be portable and operable by just one person
6) It should be easy to use

To work with cryptography we need a couple of definitions. We can define $P$ as the **plaintext space** of all the possible messages $ptx \in P$, usually $P \subseteq \{ 0,1 \}^{l}$. The **ciphertext space** is the set $C \subseteq \{ 0,1 \}^{l'}$ of all the possible ciphertext $ctx \in C$ and, finally, the key space $K \subseteq \{ 0,1 \}^{\lambda}$ is the set of keys.

An **encryption function** is defined as a function $\mathbb E: P\times K \to C$ with it's inverse operation being the **decryption function** $\mathbb D: C\times K \to P$. 

>[!note]
To be a correct encryption scheme we need for all $ptx \in P,k,k'\in K$ such that $\mathbb D(\mathbb E(ptx,k),k') = ptx$

