---
tags:
  - probability
---
Probability deals with the branch of mathematics that has to do with uncertainty. Here the sets of possible worlds is called the **sample space**. This space is represented with $\Omega$ and the elements  inside of it with $\omega$.

A fully specified **probability model** associates a numerical probability $P(\omega)$ with each possible world. The basic axioms of probability theory states that every possible world has a $P \in (0,1)$ and the set of possible worlds is $1$
$$
0\leq P(\omega) \leq 1 \qquad \sum P(\omega) = 1
$$
>[!note]
>Probabilistic assertions are not usually about worlds, but just elements in a set.

These sets of elements are called **events** or **propositions**. For any proposition $\phi, P(\phi) = \sum_{\omega \in \phi} P(\omega)$.

Probabilities such as $P(\omega), \omega\in \phi$ are known as **unconditional** probabilities; they refer to degrees of belief in proposition in the absence of any other information. When there is some **evidence** of other information we are dealing with **conditional** probability. These last are written as
$$
P(a|b) = \frac{P(a \land b)}{P(b)}
$$
### Random variables

Every random variable is a function that maps from the domain of possible worlds $\Omega$ to some range. So assign a value to a variable from its range we say
$$
P(X=x)
$$
