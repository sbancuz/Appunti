---
tags:
  - security
---
A CSPRNG is a deterministic function $\text{PRNG}: \{ 0,1 \}^{\lambda} \to \{ 0,1 \}^{\lambda + l}$ whose output cannot be distinguished from an uniform random sampling of $\{ 0,1 \}^{\lambda + l}$ in polynomial [[Complexity of an algorithm]]. $l$ is called the **stretch**. 

>[!Warning]
>This is an [[NP-complete]] problem, so they don't exist

We only have candidates build from **pseudorandom permutation** defined from some **pseudorandom function**.
### Random function

A random function is defined as $F = \{ f:\{ 0,1 \}^{in} \to \{ 0,1 \}^{out} \}$ where a uniformly random sampled $f \gets F$ can be encoded by a $2^{in}$ entries table, each $out$ bits wide. 
### Pseudorandom function

A function $\text{prf}_{se ed } : \{ 0,1 \}^{in} \to \{  0,1 \}^{out}$ taking an input and a $\lambda$ bits seed. The entire pseudo random number generator is described by that seed.
### Pseudorandom permutation

This is a **bijective** PRF that $\text{prf}_{seed} : \{ 0,1 \}^{len} \to \{ 0,1 \}^{len}$

>[!warning]
>Again, there are none

