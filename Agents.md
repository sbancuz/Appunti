---
tags:
  - artificial_intelligence
---
An agent is anything that can be viewed as perceiving the environment through **sensors** and act upon it through **actuators**. We use the term **precept** to refer to the content an agent's sensors are perceiving.
For this reason an agent it's described by it's function $f(\dots)$ that maps a sequence of perceptions to an action. 

Foe each possible percept sequence, a rational agent should select an action that is expected to maximize its [[performance measure]], given the evidence provided by the percept sequence and whatever built-in knowledge the agent has.
```math
||{"id":672843645648}||


```
An agent can be considered intelligent if it can act rationally given it's knowledge up to that moment.

We also need to distinguish rationality from omniscience, rationality aims to maximize the **expected** performance, while perfection would maximize the **actual** performance. Our definition of [[Artificial intelligence#Rational thought]] does not require omniscience because the rational choice depends only on the percept sequence **to date**. Doing actions in order to modify future percepts is called **information gathering**.  

If an agent relies only on prior knowledge of its designer rather than on its own percepts and learning processes, we say that the agent lack **autonomy**.
### Environment

From the perspective of an agent the environment can be:
- fully/partially observable
- single/multi agent -> roomba vs chess
- deterministic or not -> stochastic iff we deal explicitly with probabilities
- episodic or sequential
- static or dynamic
- discrete or continuous
- known or unknown -> this is not actually a property of the environment, but it represent the designers vision and knowledge of the environment

![[AI environment.png]]
### Structure of agents

The job of AI is to design an agent program that implements the agent function -- the mapping from percepts to actions. We assume this program will run on some sort of computing device with physical sensors and actuators -- we call this the **agent architecture**
$$
agent = architecture + program
$$

In general the architecture makes the percepts from the sensors available to the program. We can define two types of agents:
- [[Rational agents]]
- [[Logical agents]]

