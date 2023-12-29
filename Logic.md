---
tags:
  - artificial_intelligence
---
A logic represents how a knowledge base expresses information and it's composed of sentences. These sentences are expressed according to a **syntax** that describes the representation language. A logic must also define **semantics** -- i.e. the meaning of the sentences. 

Each sentence must exist in **possible world** or **model** to be more precise. A model is a mathematical abstraction that has a fixed truth value for every relevant sentence.

If a sentence $\alpha$ is true in model $m$ then we say that $m$ **satisfies** $\alpha$ or that $m$ **is a model of** $\alpha$.
$$
M(\alpha) \gets \text{All models of }\alpha
$$
Now we have to define what logical reasoning is, this involves the relation of logical **entailment** between sentences -- the idea that a sentence **follows logically** from another one.
$$
\alpha \vDash \beta \text{ iff } M(\alpha) \subseteq M(\beta)
$$
Entailment can be applied to derive conclusions -- that is, to carry out **logical inference** or **model checking** because it emulates all possible models $M(KB) \subseteq M(\alpha)$

If a inference algorithm $i$ can derive $\alpha$ from KB we write
$$
KB \vdash _{i} \alpha 
$$
An issue to consider is if the KB is **grounded** -- if the logical reason is also true in the real world. 
### Properties
- Soundness $\to$ an inference algorithm can only derive entailed sentences
- Completeness $\to$ it can derive any sentence that is entailed
### Types of logic
- [[Propositional logic]]
- [[First order logic]]