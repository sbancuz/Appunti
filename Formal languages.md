---
tags:
  - compilers
---
### Alphabet

Finite set of elements and can be defined as a string, a word or a phrase
$$
\begin{align}
\Sigma &= \{ a_{1},a_{2},\dots,a_{k} \} \\
|\Sigma| &= k
\end{align}
$$
### String

Is an ordered set of atomic elements, possibly repeated. The length of a string is the number of elements that contains
$$
\begin{align}
|bbc| = 3 \\
|bbc|_{b} = 2
\end{align}
$$
and two strings are considered equals when they have the same length and their elements orderly coincide. 

#### Operation on strings
$$
x = a_{1}a_{2}a_{3}\dots a_{h}, y=b_{1}b_{2}\dots b_{k}
$$
- Concatenation $\to x.y = a_{1}a_{2}\dots a_{h}b_{1}b_{2}\dots b_{k}$
- Empty string $\to |\epsilon| =0$
- Substring $\to x = uyv$ where $u$ is a prefix, $v$ is a suffix and $y$ is the substring
- Mirroring $\to x=atri, x^{R} =itra$
- Repetition $\to x^{m} = x\dots x_{m}$

Both the power and the mirroring precedes concatenation.
### Language

Finite or infinite set of strings
$$
\begin{align}
\sigma = \{ a,b,c \} \\
abc,aabc,ac,bbb
\end{align}
$$
It can also be defined as an unordered set $L$ of strings that are in turn sequences of atomic elements. It's cardinalitiy can be either finite or infinite.
$$
\begin{align}
L_{1} &= \{ ab,ac \} \\
L_{1} &= \{ abc,aabb cc,abcabc \}
\end{align}
$$
#### Prefix free language

Is a language where there isn't any string that is a prefix of another string of the language. So 
$$
L \cap \text{prefix}(L) = 0
$$
#### Universal language

Is the set of all the strings defined over the alphabet $\Sigma$ of any length

#### Operations

An operation defined on a language applies to each string in the language.
$$
L^{R} = \{ x|x=y^{R} \land y \in L \}, prefix(L) = \{ y|x=yz \land x \in L \land y,z \neq \epsilon \}
$$
- concatenation $\to L_{1}L_{2} = \{ xy|x\in L_{1} \land y \in L_{2} \}$
- power $\to L^{m} = L^{m-1}L$
- string of a finite length $\to L = \{ \epsilon,a,b \}^{3} = \{ \epsilon,a,b,aa,ab,bb,aaa,\dots,b b b  \}, k = 3$
- set theoretic operations (Union, intersection, complement, equality, inequality)
- star operator $\to L^{*} = \cup_{k} L^{k}$
- cross operator $\to L^{+} = \cup_{k= 1}L^{k}$
- quotient operator $\to L = L_{1}/L_{2} = \{ y|(x-yz \in L_{1}) \land z \in L_{2} \}$

--> [[Regular expressions]]
### Regular languages

These are languages which are recognized by a [[Finite state automata]] and they are a sub-family of the languages recognizable by a [[Turing machine]]

### Free languages

These are a sub-family of the languages recognized by a [[Turing machine]] which have polynomial time [[Complexity of an algorithm]]