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
### Concepts
- Inference
	Now we have to decide whether KB $\vDash \alpha$ for some sentence $\alpha$, to do this we just enumerate the models and check $\alpha$ is *true* in every model in which KB is *true*. This approach is not the best one because it's extremely slow, but it works.

- Logical equivalence
	Two sentences $\alpha$ and $\beta$ are equivalent if they are true in the same set of models. This is represented as $\alpha \equiv \beta$ . Another definition is if that $\alpha$ and $\beta$ both entail each other.
$$
\alpha \equiv \beta \text{ iff } \alpha \vDash \beta \land\beta \vDash  \alpha
$$
- Validity
	A sentence is valid if it is true in all models, these sentence are also known as **tautologies**.

- Satisfiability
	A sentence is satisfieable if it is true in some model. In logic the problem of checking if a sentence is satisfiable is known as the **SAT** problem.  
### Theorem proving

Entailment can also be done by theorem proving, i.e. applying rules of inference directly to the sentences in our knowledge base to construct proof of the desired sentence without consulting models. To determine if a sentence is valid we can use **deduction**, which is defined as 
$$
\text{For any sentences } \alpha,\beta, \alpha \vDash \beta \text{ iff the sentence }(\alpha \implies\beta) \text{ is valid}
$$
![[logic eq.png]]

Validity and satisfiability can be used together:
- $\alpha$ is valid iff $\lnot \alpha$ is unsatisfiable
- $\alpha$ is satisifiable iff $\lnot \alpha$ is not valid
- $\alpha \vDash \beta$ iff the sentence $(\alpha \land \lnot\beta)$ is unsatisfiable

The technique of checking the unsatisfiability of $(\alpha \land \lnot \beta)$ is called **proof by contradiction**.

Inference rules can also be applied to derive **proofs** -- chains of conclusions that leads to the desired goal. The best known rule is **Modus Pones** and is written as
$$
 \frac{\alpha\implies\beta,\alpha}{\beta}
$$
This means that $(\alpha\implies\beta), \alpha$ are given and $\beta$ is inferred. Another useful rule is **And elimination**
$$
\frac{\alpha \land \beta}{\beta}
$$
To begin a proof problem we need to define:
- Initial state
- Actions $\to$ composed of the inference rules applied to all the sentences
- Result $\to$ result of actions
- Goal
#### Proof by resolution

For now we've seen that the inference rules already covered are all *sound*, but they are not *complete*. To make the proof complete we can add a single inference rule called the **resolution** -- yields a complete inference algorithm when coupled with any complete [[Search problem#Search strategies]].

One such resolution is the **unit resolution** inference rule that states
$$
\frac{l_{1}\lor\dots \lor l_{k}, \qquad m}{l_{1}\lor\dots l_{i-1}\lor l_{i+1}\lor \dots l_{k}}
$$
where each $l$ is a literal and $l_{i}$ and $m$ are complementary literals. Thus the resolution takes a **clause** -- disjunction of literals -- and a literal and produces new clause.

>[!warning]
>You can resolve only one pair of complementary literals at a time. Also the resulting clause should contain only one copy of each literal.

The removal of multiple copies of literals is called **factoring**.

>[!example]
>$(A\lor B)$ with $(A\lor  \lnot B)$ we can obtain $(A\lor A) \implies A$
##### Conjunctive normal form

The problem with the resolution rule can only be applied to clauses, but we can circumvent this by just converting any sentence of propositional logic to a conjunction of clauses. A sentence like this is said to be in **conjunctive normal form**. This can be done in 4 steps
1) Eliminate $\alpha\iff \beta$ replacing it with $(\alpha \implies \beta) \land (\beta \implies \alpha)$
2) Eliminate $\alpha \implies \beta$ replacing it with $\lnot \alpha \lor\beta$
3) Apply the "$\lnot$" only in the literals, this can be done with [[De Morgan Law]]
4) Apply the distributivity law to all $\land,\lor$ 

![[cnf grammar.png]]
##### Resolution

To resolve a proof we go by contradiction, that is to show that KB $\vDash \beta$ we show that $(\text{KB} \land \lnot \alpha)$. The first thing to do is to convert everything to CNF, then the resolution rule is applied to the resulting clauses. Each pair that contains complementary clauses is resolved to produce a new clause. This process repeats until either:
- no new clauses can be added, in which case KB does not entail $\alpha$
- two clauses resolve to yield the empty clause, in which case KB entails $\alpha$

To show that this algorithm is complete we need to introduce the **resolution clause** $RC(S)$ of a set of clauses $S$ -- a set of all clauses derivable by repeated application of the resolution rule. It's easy to see that $RC(S)$ must be finite, hence the algorithm always terminates. This is called the **ground resolution theorem** that more formally states that:
	If a set of clauses is unsatisfiable, then the resolution closure of those clauses contains the empty clause.

![[example res.png]]
##### Horn clause

In many practical situations the full power of the resolution is not need because the clauses satisfy certain restrictions that can be resolved by more efficient methods.

The Horn clause is one such case, which is a disjunction of literals of which *at most one is positive.* So all definite clauses are Horn clauses, as are clauses with no positive literals -- **goal clauses** that is.

Knowledge bases containing only definite clauses are interesting for three reasons:
1) Every definite clause can be written as an implication whose premise is a conjunction of positive literals and whose conclusion is a single positive literal
2) Inference can be done through [[Forward chaining algorithm]] and [[Backward chaining algorithm]].
3) Deciding entailment with Horn clauses can be done in linear time to their size