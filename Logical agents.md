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
### Planning

The next thing we have to model is how the agent should plan its actions. To represent these actions we can use a **factored representation** using a family of languages called **PDDL** which allows to represent more general actions with only a single action.

In PDDL, a **state** is represented as conjunction of ground (no variable) atomic single predicate) fluents (aspects of the world that change). It also uses [[First order logic#Database semantics]]. 

An **action schema** represents a family of ground actions. A schema consists of the action name, a list of all the variables used in the schema, a **precondition** and an **effect**. We can choose constants to instantiate the variables yielding a ground action.

>[!example]-
>$$
>\begin{align}
> Action(&Fly(p, from, to),  \\
> & \text{Precond:At}(p, from) \land Plane(p) \land Airport(from) \land Airport(to) \\
> & \text{Effect:}\lnot\text{At}(p,from) \land \text{At}(p,to))
>\end{align}
>$$

A ground action $a$ is **applicable** in state $s$ if $s$ entails the precondition of $a$, that is, if every positive literal in the precondition is in $s$ and every negated literal is not. The **result** of an action on a state $s$ is defined as the new state $s'$. 

>[!note]
>PDDL deals with the frame problem -- what is changed after performing an action -- by only changing what is specified in the effects. The negations in the effect can be put in the $\text{Delete}$ list for the state $s$ and the positive one are in the $Add$ list. All the other knowledge in the KB remains untouched.
#### PDDL Extensions

In PDDL you can use:
- negative literals in preconditions and goal
- predicates for inequality and equality
- algebraic expressions
- state constraints
#### Classical planning algorithms

The description of a planning problem provides an obvious way to search from the initial state through the space of states, looking for a goal.
#### Forward planning

We can solve planning problems by applying any of the [[Informed search strategies]]. The states in this search state space are ground states, where every fluent is either true or not. The **applicable** actions are the instantiations of the actions schema. This approach has clear computational problems, the state space is just too big and the branching factor is huge.
### Backward planning

Here we start from the goal and apply the actions backward until we find a sequence of steps that reaches the initial state. At each step we consider only the **relevant actions**, thus reducing the branching factor significantly. A relevant action is defined as an action that involves the goal without negating it.

The problem with this approach is that since it doesn't use ground states, it's hard to come up with effective heuristics.
### SAT plan

SAT planners operate by translating a PDDL problem description into propositional form. This is done in steps:
1) Propositionalize the actions $\to$ for each action schema, form ground proposition by substituting constants
2) Add action exclusion $\to$ no 2 action can be performed at the same time
3) Add precondition axioms $\to$ for each ground action $A$ at time $t$ add the axiom $A^{t} \implies Pre(A)^{t}$
4) Define the initial state $\to$ assert $F^{0}$ for every fluent $F$ in the initial state and $\lnot F^{0}$ to the rest
5) Propositionalize the goal $\to$ the goal becomes a disjunction over all of its ground instances
6) Add successor state axioms $\to$ for each $F$ add $F^{t+1}\iff ACause F^{t} \lor (F^{t}\land \lnot ANotCausesF^{t})$

The model checking for these planners is done incrementally, we choose a max length of the solution, then if we can't find a solution we try again with a greater length.
### Non deterministic planners

Up until now we worked within an ideal world, but in the real one we face partial observability, non-deterministic and unknown environments. This affects the way we represent the agent perception of the world, we represent this new view in **belief states** -- the set of possible states the agent might be in.  

To perceive unknown information from the environment we have to augment the PDDL by adding the $\text{Percept}$ function that takes as input what we are actually tying to get information and the precondition to do so. 

>[!warning]
>There is much more in this chapter, but is not covered in the lectures so....
### Uncertainty

Agents in the real world need to handle **uncertainty**, whether partial observability or non determinism. To resolve this problem we used belief states to represent each possible state the agent might be in and acted accordingly. Although this approach works, it has a couple of drawbacks:
- the agent must consider all the possible explanation for its sensor observations, no matter how unlikely
- a correct contingent plan for all the possible cases can grow exponentially large
- sometimes a completely contingent plan just doesn't exist

If the agent's knowledge cannot guarantee some outcome, it can try to provide a **degree of belief** that certain goals will be accomplished. So when planning a solution, the right thing to do, i.e. the rational decision, depends on both the relative importance of various goals and the likelihood that they will be achieved. Our main tool to deal with this uncertainty is [[Probability theory]].

To make choices on the best course of actions, an agent must first have preferences among different possible outcomes of the various plans. We can use [[Utility theory]] to represent preferences and reason quantitatively with them.

The combination of these two needs is [[Decision theory]]. In order to reduce the number of probabilities needed to specify a full joint distribution we employ a [[Bayesian network]] to represent the dependencies among variables.