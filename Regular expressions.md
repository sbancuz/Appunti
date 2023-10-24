---
tags:
  - compilers
---
Regular languages are the simplest family of formal languages. This family can be defined in different ways:
- algebraically
- by generating a grammar
- by recognizing machines

### Regular expressions

Are strings $r$ defined over the letters of the terminal alphabet $\Sigma$ and that contains a dew metasymbols
$$
. \ \cup \ * \ \emptyset \ ()
$$
A regex e is a language $L_{e}$ over $\Sigma$ according to the following table

| Regex | Language |
| - | - |
| $\epsilon$ | $\{ \epsilon \}$ |*
| $a \in \Sigma$ | $\{ a \}$ |
| $s\cup t$ | $L_{s}\cup L_{t}$ |
| $st$ | $L_{s}L_{t}$ |
| $s^{*}$ | $L_{s}^{*}$ |

| Syntax | Match |
| - | - |
| x | the 'x' character |
| . | any character |
| [xyz] | x or y or z |
| [a-z] | any character between a and z |
| [\^a-z] | any character except between a and z |
| R* | any occurrences of R |
| R+ | one or more occurrences of R|
| R? | zero or one occurrences of of R|
| R \| S| either R or S|
|R {n, N} | a number of occurrences of R ranging from n to N|
|\^R | R at the beginning of the line|
| R$ | R at the end of the line|
| (R) | capture groups |

**REG** is defined as the collection of all regular languages.
**FIN** is the collection of all languages of finite cardinality.

>[!warning]
>Both REG and FIN are set of sets of strings

And every finite language is regular, because it is the finite union of finitely many strings.

Two regex are equivalent if they define the same language.
#### Sub-expressions of a regex

The parents in a regex define the precedence of operations, hence depending on the position of the parenthesis the meaning of the regex changes.

The union and iteration operators that occur in a regex correspond to some possible alternatives. By choosing one, a new regex that defines a smaller language than the original is obtained.

Given a regex $e_{1}$, one can always derive another regex $e_{2}$ by replacing a sub-expression of the regex $e_{1}$ with one of the possible choices. 
$$
e_{1} \implies e_{2} \text{ if } e_{1} = \alpha\beta\gamma, \ e_{2} = \alpha \delta \gamma
$$
where $\beta$ is a sub-expression of $e_{1}$, $\delta$ is a sub-expression of $e_{2}$ and $\delta$ is a choice of $\beta$

### Ambiguity of regex

A string may be obtained by two derivations, that differ not only in the order of choices, but in a more substantial way.
$$
\begin{align}
(a\cup b)^{*}a(a\cup b)^{*} &\\
(a\cup b)^{*}a(a\cup b)^{*} &\implies (a\cup b)a(a\cup b)^{*} \implies aa(a\cup b)^{*} \to aa\epsilon \implies aa \\
(a\cup b)^{*}a(a\cup b)^{*} &\implies \epsilon a(a\cup b)^{*} \implies \epsilon a(a\cup b) \to \epsilon aa \implies aa \\
\end{align}
$$
A regex can be considered ambiguous if the corresponding marked regex $f_{\#}$ generates two marked strings $x$ and $y$ such that, if the indices are removed, the unmarked strings obtained are identical.

It's better to have non ambiguous regexes if possible. It's always possible to disambiguate a regex.
$$
\Sigma^{*} a \Sigma^{*}= (a|b)^{*}a(a|b)^{*} = \Sigma^{*}ab^{*}
$$
### Translate to [[Finite state automata]]

The local set of the language is:
$$
\begin{align}
\text{initials } \to& Ini(L) = \{ a \in \Sigma | a \Sigma^{*}\cap L \neq \emptyset \} \\
& Ini(\emptyset) = \emptyset \\
& Ini(\epsilon) = \emptyset \\
& Ini(a) = \{ a \} \\
& Ini(e \cup e') = Ini(e) \cup Ini(e') \\
& Ini(ee') = \text{if } Null(\epsilon) \text{ then } Ini(e) \cup Ini(e') \text{ else } Ini(e) \\
& Ini(e^{*}) = Ini(e^{+}) = Ini(e)\\
\text{finals } \to& Fin(L) = \{ a \in \Sigma | \Sigma^{*} a \cap L \neq \emptyset \} \\
& Fin(\emptyset) = \emptyset \\
& Fin(\epsilon) = \emptyset \\
& Fin(a) = \{ a \} \\
& Fin(e \cup e') = Fin(e) \cup Fin(e') \\
& Fin(ee') = \text{if } Null(\epsilon) \text{ then } Fin(e) \cup Fin(e') \text{ else } Fin(e) \\
& Fin(e^{*}) = Fin(e^{+}) = Fin(e) \\
\text{digrams } \to& Dig(L) = \{ x \in \Sigma^{2} | \Sigma^{*} x \Sigma^{*} \cap L\neq \emptyset \} \\
& Dig(\emptyset) = \emptyset \\
& Dig(\epsilon) = \emptyset \\
& Dig(a) = \{ a \} \\
& Dig(e \cup e') = Dig(e) \cup Dig(e') \\
& Dig(ee') = Fin(e) \cup Fin(e') \cup Fin(e) Ini(e) \\
& Dig(e^{*}) = Dig(e^{+}) = Dig(e) \cup Fin(e) Ini(e)\
\end{align}
$$

We define a regexp that generates an empty string as 
$$
\begin{align}
&Null(\emptyset) = false \\
&Null(\epsilon) = true \\
&Null(a) = false \\
&Null(e \cup e') = Null(e) \lor Null(e') \\
&Null(e  e') = Null(e) \land Null(e') \\
&Null(e^{*}) = true \\
&Null(e^{+}) = Null(e)
\end{align}
$$

There are a few algorithms that can perform this transformation:
- [[Thompson]] 
- [[Berry-Sethi]]
### Complement and intersection

Regex may also contain the operators of complement, intersection and set difference.
$$
\begin{align}
\text{ if } L, L' \in REG \text{ then }& \lnot L \in REG \land L \cap L'  \in REG \\
\lnot &= \Sigma^{*} \setminus L
\end{align}
$$
Using [[De Morgan Law]] we can rewrite the intersection as a complement and union. 
$$
L \cap L' = \lnot(\lnot L\cup \lnot L')
$$