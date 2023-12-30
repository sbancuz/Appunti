---
tags:
  - artificial_intelligence
---
First order logic is a combination of the declarative, context independent and compositional nature of [[Propositional logic]] and the more expressive representational ideas from natural languages while avoiding its drawbacks.

First order logic is composed of **objects** -- usually nouns -- and **relations** -- verbs and adjectives. Some relations can be though as **functions** that map one value for a given input.
### Models

Models in a logical language are the formal structures that constitute the possible worlds under consideration. Each model links the vocabulary of the logical sentences to elements of the possible world, so that the truth of any sentence can be determined. Model for FOL can carry objects in their **domain**. 

>[!warning]
>The domain must be non empty. Also models require total functions -- all their input map to some output
### Symbols

The basic elements of the FOL are the symbols that stand for objects, relation and functions. There are 3 kinds:
- constants $\to$ objects
- predicate $\to$ relations
- functions

![[fol symbols.png]]

Every model must provide the information required to determine if any given sentence is true of false. Thus each model includes an **interpretation** that specifies exactly which objects, relations and functions are referred to by the constant, predicate and function symbol.
### Quantifiers

Quantifiers let us express properties on entire collection of objects, instead of enumerating them by name.
#### Universal quantifier

The universal quantifier $\forall {}  {}$ is usually pronounced "*for all*" and is represented as
$$
\forall {x} King(x) {\implies Person(x)} 
$$
The symbol $x$ is called a **variable** -- a new term of the sentence.
### Existential quantifier

If something needs to hold only for some object we use the existential quantifier
$$
\exists x Crown(x) \land OnHead(x, Jhon)
$$
and is pronounced as "*There exists an $x$ such that*". More precisely it says that for the quantifier to be true at least one extended interpretation must be true.
#### Connection between the two quantifiers

By moving a negation in a sentence though a quantifier you can pass from one to the other without changing the meaning of the sentence. For example asserting that everyone dislikes parsnips is the same as asserting there does not exist someone how likes them. With [[De Morgan Law]] we can assert that

![[quant.png]]
### Equality

A new symbol in FOL is the equality symbol that signifies that two terms refer to the same object.
$$
Father(John) = Henry
$$
### Assertions

The sentences added to a knowledge base are called **assertions**, this is done with the $\text{Tell}$ function. You can also query assertions from a knowledge base using the $\text{Ask}$ function. There is also another "standard" function called the $\text{AskVars}$ that returns the values that a variable can be, this list is called a **binding list**. 

>[!warning]
>A binding list is usually reserved for Horn clauses
### Axioms

Axioms are associated with purely mathematical domains, but they are needed in all domains. They provide a basic factual information from which useful conclusions can be derived. Some axiom that are in the form $\forall {x,y} P(x,y) {\iff} \dots$ can be viewed as **definitions**. Not all logical sentences about a domain are axioms, some are **theorems** -- that is, they are entailed by the axioms. This helps to reduce the complexity of the KB.