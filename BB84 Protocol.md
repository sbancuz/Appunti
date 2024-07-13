---
tags:
  - quantum
---
This is a QKD encryption scheme proposed in 1984. This encryption scheme takes advantage of the fact that it's **not possible** to exactly reconstruct the state of an unknown [[Qubit]]
```math
||{"id":1219572858298}||


```
This is due to the fact that the [[Measurement]] is a non-reversible operation, and as such we must measure the [[Bloch sphere]] in a precise way to decode the message.
### Scheme

Alice will transmit a sequence of qubit, chosen among $4$ [[Qubit]] belonging to $2$ **complementary bases** -- on orthogonal axis on the [[Bloch sphere]]. Bob will perform a sequence of measurements on a random sequence of basis. If Bob measures the qubit with the right basis then we can correctly reconstruct the information, otherwise that *bit* of information will be irreversibly lost. Alice then will transmit her choice of basis and Bob will discard all the measurements he got wrong.