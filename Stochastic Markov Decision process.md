---
tags:
  - machine_learning
---
In stochastic [[Markov Decision processes]] we can describe a policy $\pi$ as a **distribution over all the actions** given a particular state
$$
\pi(a | s) = \mathbb P[a|s]
$$
>[!Note]
>Remember that the Markov decision processes don't need to know the full history, just the current state

This means that we can define the value function, that gives the **utility** of each state.
$$
V^{\pi}(s) = \mathbb E[v_{t} | s_{t} = s]
$$
For **control** purposes it's easier to consider **the value of each action** in each state. The action value function $Q^{\pi}(s,a)$ is the expected return starting from state $s$, taking action $a$ following a policy $\pi$
$$
Q^{\pi}(s,a) = \mathbb E_{\pi}[v_{t} | s_{t} = s, a_{t} =a ]
$$
### Bellman expectation equation

The state-value function can be decomposed again into immediate reward plus discounted value of successor state
$$
V^{\pi}(s) = \sum_{a}\pi(s|a) \left( R(s,a) + \gamma \sum_{s'}P(s'|s,a) V^{\pi}(s') \right)
$$
That can be concisely rewritten as
$$
V^{\pi}  = R^{\pi} + \gamma P^{\pi}V^{\pi} \implies V^{\pi} = (I - \gamma P^{\pi})^{-1}R^{\pi}
$$
This means that we can also decompose the action-value function
$$
Q^{\pi}(s,a) = R(s,a) + \gamma \sum_{s'} P(s'|s,a)\sum_{a'}\pi(s',a')Q^{\pi}(s',a')
$$
