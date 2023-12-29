---
tags:
  - artificial_intelligence
---
A logical agent is capable of using logical sentences to represent knowledge of states and actions.
### Knowledge based agents

In AI, **knowledge based agents** use a process or **reasoning** over an internal **representation** of knowledge to decide what actions to take. [[Rational agents]] know things, but in a very limited way, they just have the knowledge of their available actions, but they don't know general facts.

>[!example]
>I can give to a logical agent the goal to reach a city in the world, but to the rational agent, to give the exact same task, i have to give as a goal the explicit set of cities in the world.

A KB agent has only 2 basic operation:
- $\text{Tell} \to$ insert into the KB some knowledge in form of sentences
- $\text{Ask} \to$ query the KB for some fact

The central component of a knowledge based agents is it's knowledge base -- a set of **sentences**. Each sentence is expressed in a language called a **knowledge representation language**. For this course we will consider only [[Propositional logic]] and [[First order logic]].