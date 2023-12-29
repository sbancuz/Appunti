---
tags:
  - artificial_intelligence
---
### Syntax

The atomic sentences consist of a single propositional symbol. Each such symbol stands for a proposition that can be true or false. **Complex sentences** are composed from simpler ones, held together by parentheses and **logical connectives**. 

| Symbol | Meaning |
| ---- | ---- |
| $\lnot$ | Negation |
| $\land$ | Conjunction, both term must be true for the sentence to be true |
| $\lor$ | Disjunction, either of the terms must be true for the sentence to be true |
| $\implies$ | Premise $\implies$ Conclusion |
| $\iff$ | If and only if |
#### Backus Naur form

![[BNF.png]]
### Semantics

The semantics define the truthfulness of a sentence, in particular a model sets the truth value for every propositional symbol. This means that propositional logic must specify how to compute the truth of atomic sentences and how to recursively compute the truth of the sentences. After computing all the truths we can define a **truth table** that enumerates all of them.

![[proplogic.png]]
### Knowledge base

To create a knowledge base we can focus on the immutable aspects of the model we are representing, leaving the mutable one for later selection. Each aspect can be represented with a symbol.
### Inference

Now we have to decide whether KB $\vDash \alpha$ for some sentence $\alpha$, to do this we just enumerate the models and check $\alpha$ is *true* in every model in which KB is *true*. This approach is not the best one because it's extremely slow, but it works.
### Theorem proving

Entailment can also be done by theorem proving, i.e. applying rules of inference directly to the sentences in our knowledge base to construct proof of the desired sentence without consulting models. 