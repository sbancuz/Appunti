---
tags:
  - compilers
---
A FSM can define a recognition algorithm. The application of this algorithm $x$ is indicated as $\alpha(x)$ and the [[Formal languages]] described by this automata is $L(\alpha)$

>[!warning]
>If the language is semi-decidable then it may happen that for some uncorrect strings the algorithm does not terminate 

Almost all of the problems of interest here, have solutions with a relatively low time [[Complexity of an algorithm]], which is in most cases the length of a string.

The automaton analyzes the input and executes a series of moves. Each of which depends on the symbols currently pointed by the heads and by the state. A move can be:
- Shifting the input head to the left/right
- Replacing the current memory symbol b a new one and shifting the memory head
- Changing the current state

>[!note]
>Not all the operations are always allowed

An FSM is considered to be **deterministic**, this means that there is at most one possible move for every configuration. If this is not the case we are talking about [[Non-deterministic finite state automaton]] The input string is:
- Accepted -> The FSM has reached the final state
- Rejected -> The FSM cannot do any more moves

A FSM consists of 5 elements:
- $Q$ -> the set of states
- $\Sigma$ -> the input alphabet
- $\delta:(Q\times\Sigma)\to Q$ -> the transition function
- $q_{0}$ -> the initial state
- $F \subseteq Q$ -> the set of final state

An FSM can recognize multiple [[Formal languages]], all these languages are grouped in a family of recognized languages of the automaton. 
### Configuration

A configuration is the set of the three components that determine the behaviour of the automaton 
- The unread part of the input
- The contents and position of the memory tape and head
- The current state
### State transition graph

This graph is a directed graph that represents the automaton and consists of the following:
- Nodes -> represents the states
- Arch -> represents the moves

This has a **unique** initial and **non unique** final states. This graph can also be represented by an incidence matrix.

![[fms.png]]

### Minimal automaton

For every finite state language there exists one, and only one, deterministic finite state recognizer that has the smallest possible number of states. This type of FSM doesn't have indistinguishable states