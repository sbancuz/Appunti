---
tags:
  - security
---
In a **perfect cipher**, for all $\text{ptx} \in P$ and $\text{ctx}\in C$
$$
Pr(\text{ptx sent} = \text{ptx} )= Pr(\text{ptx sent }=\text{ptx} | \text{ctx sent} = \text{ctx})
$$
In other words, seeing a ciphertext gives no information on what the plaintext corresponding to the ciphertext could be.
### Shannon theorem

Any symmetric cipher $\langle P,K,C,\mathbb E, \mathbb D \rangle$ with $|P|=|K|=|C|$ is perfectly secure iff:
- every key is used with probability $\frac{1}{|K|}$
- a unique key maps a given plaintext into a given ciphertext

>[!example]
>Assume $P,K,C$ to be a set of binary strings. The encryption function draws a **uniformly random** fresh key $k$ each time it's called and computes $\text{ctx} = \text{ptx} \oplus k$
### Problems

It's quite clear that, even though these schemes are undecipherable, even with today's technology, they are not practical. The main problem with them is the key distribution, so it becomes unpractical