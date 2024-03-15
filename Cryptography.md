---
tags:
  - security
---
It's the study of the techniques to allow secure communication and data storage in presence of attackers. With cryptography we want to ensure:
- Confidentiality $\to$ data can be accessed only by chosen entities
	There are multiple ways an attacker can accesses unauthorized data: eavesdropping, it knows already a set of plaintexts or, it may tamper with the data trying to decrypt it. To solve there are [[Perfectly secure cipher]] and [[Computationally secure cipher]]

- Integrity $\to$ prevent tampering or replays
	To achieve this we either design an intrinsically non tamperable cipher, which is quite the task, or simply add some information using [[Message authentication codes]]. Testing integrity on the whole file requires us to compare it bit by bit with an intact copy, ideally we would want fixed length strings that represent the whole file. These are just [[Cryptographic hash]]. To use them with [[Message authentication codes]] just produce a tag hashing together the message and a secret string.

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
### Diffie-Hellman key agreement

To make asymmetric keys feasible we need a way to share secret values, with only public messages. This means that an attacker can eavesdrop on **anything**, but it mustn't be able to taper the data.

So, let $(G,\times )\equiv \langle g\rangle$ be a finite cyclic group, and two numbers $a,b$ sampled from $\{  0,\dots,|G|-1\}$. Given $g^{a},g^{b}$ finding $g^{ab}$ costs more than $poly(\log|G|)$

The agreement works in this way:
- Alice picks $a$ and sends $g^{a}$ to Bob, he then computes $g^{ba}$
- Bob picks $b$ and sends $g^{b}$ to Alice, she then computes $g^{ab}$

>[!tip]
>Since $(G,\times)$ is commutative, $g^{ab} = g^{ba}$ 
### Public key encryption

Different keys are employed in encryption/decryption. In this scheme it's computationally hard to 
- decrypt a chipertext without the private key
- compute the private key given only the public key

![[pb key encr.png]]

One of the most widespread chiper still used today is the [[RSA Cryptosystem]]. Too bad this does not hold to quantum computers. An alternative that was more used before due to patent problems was the Elgamal encryption scheme.

The main objective of asymmetric cryptosystems is to encapsulate and share the keys of a symmetric cryptosystems. This is because asymmetric ones are way more computationally complex than their symmetric counterpart, and also they tend to use more space.