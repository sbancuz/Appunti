---
tags:
  - compilers
aliases:
  - parser
---
Given a [[Free grammars]] $G$, the parser:
1) reads the source
2) if the string belongs to the language $L$ then either:
	-  exhibits a derivation
	-  builds a syntax tree
3) else stops and notifies of the error
### Bottom-up analysis

Rightmost derivation in inverse order tree from leaves to root through reductions.
### Top-down analysis

Leftmost derivation in direct order tree from root to leaves through expansions. This can easily be done by means of recursion and reflects the machine transitions.

>[!warning]
>This does not work when the symbol sets on the arcs that leave the same states are not disjoint

