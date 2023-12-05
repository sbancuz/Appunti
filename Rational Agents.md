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



### Types of agents

The is no unique solution but there are some approaches to build agents of increasing complexity. You could try to encode your knowledge, but that could be either too complex or you could be just not skilled enough in the topic your training your agent.  

![[Agent coplexity.png]]

### Simple reflex agent

 This is based on rules encoded when building the agent.
```pseudo
   \begin{algorithm}
    \begin{algorithmic}
      \PROCEDURE{Simple-reflex-agent}{$percept$} 
	    \State $\textbf{persistent}:$ rules, a set of condition-action rules
		\STATE $state \gets$  \CALL{Interpret-input}{$percept$}
        \STATE $rule \gets$  \CALL{Rule-match}{$state$}
        \STATE $state \gets rule.ACTION$
	    \return{action}
      \ENDPROCEDURE
      \end{algorithmic}
    \end{algorithm}
```
The first Roomba was a simple reflex agent that detected whenever it needed to change direction if there was an obstacle in the way. 

### Model-based reflex agents

This agent can hold a state that indicate how it should behave.
```pseudo
   \begin{algorithm}
    \begin{algorithmic}
      \PROCEDURE{Model-based-reflex-agent}{$percept$} 
	    \State $\textbf{persistent}:$ \\
			transition-model, a description transitions between states and action\\ 
			sensor-model, how the environment is perceived by the actor\\ 
			rules, a set of condition-action rules\\
			action, the most recent action\\
		\STATE $state \gets$  \CALL{Update-state}{$state, percept, action, transition-model, sensor-model$}
        \STATE $rule \gets$  \CALL{Rule-match}{$state, rules$}
        \STATE $state \gets rule.ACTION$
	    \return{action}
      \ENDPROCEDURE
      \end{algorithmic}
    \end{algorithm}
```
 The next Roomba can create a model of the environment.

### Goal-based agents

This agent also asks whats the consequences of it's actions and how the environment will change.

This could be achieved with the [[Minimax algorithm]] 

--> [[Boids]]
--> [[Building a goal based agent]]
### Utility-based agents

This agents tends to maximise the utility while still achieving the goal. This could be because there might be a lot of ways to reach a certain goal, but there could be a 'best' way. 
### Learning agents

Learning allows the agent to operate in initially unknown environments and to become more competent than its initial knowledge alone might allow.

![[learning agents.png]]

