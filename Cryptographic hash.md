---
tags:
  - security
---
A cryptographic has is a function $H: \{ 0,1 \}^{*} \to \{ 0,1 \}^{l}$ for which the following problems are hard
- given $d=H(s)$, find $s$. Complexity $\mathcal O(2^{d})$
- given $s,d = H(s)$, find $r\neq s$ with $H(r)=d$.  Complexity $\mathcal O(2^{d})$
- find $r\neq s$ with $H(s)=H(r)$.  Complexity $\mathcal O(2^{d/2})$

The output bitstring is also known as the **digest**. 