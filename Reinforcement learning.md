---
tags:
  - machine_learning
---
It performs actions that affect the environment, and receiving rewards it learn to maximize its **long-term reward**. The choice of when rewarding the agent is very important, let's consider racing: you could give rewards when an agent has won the race or depending on its position. These are called **sparse** rewards because most of the time the agent doesn't receive them. A better approach to make the learning process much easier and faster would be to give rewards for going in the right direction in the track. As long as we can provide the correct reward signal to the agent, reinforcement learning provides a general way to build AI systems.

We can define the **history** as the sequence of observations, actions and rewards
$$
h_{t} = o_{0},a_{0},r_{0},\dots
$$
i.e. all the available information up to time $t$. The state $s_{t}$ then can be represented as function of the history of the agent.
The agent works by computing an action-value function mapping state-action pairs to expected payoffs
$$
Q(a_{t}, s_{t}) = \text{payoff}
$$
or state-value functions mapping to expected payoffs.
$$
V( s_{t}) = \text{payoff}
$$
Reinforcement learning assumes $Q(\dots)$ to be represented as a table, but in the real world we cannot afford to compute it exactly.

>[!note]
>Reinforcement learning should be used when we don't know the dynamics of the system we want our agent to be in, or when the environment is just too hard to be solved exactly.
### Action selection & policy

At each time step, the agent must decide what action to take. And at any given point in time the policy $\pi(st)$ select that very action. So the policy determines how actions map to the new states, and they can be:
- deterministic : this can be modeled as a functions $\pi: S \to A$ 
- stochastic : it maps the probability distribution over the actions $\pi : S,A \to R$

> [!Warning] Exploration-Exploitation dilemma
> 
To obtain a lot of reward, the agent must prefer actions that it has tried in the past and found to lead to high payoff however, to discover such action, it has to try actions that has not selected before. So there needs to be a trade-off between the exploration of new actions and the exploitation of promising ones.

The 2 main type of policies are:
- Greedy policy: that deterministically selects an action with maximal value. $\to$ [[Markov Decision processes]]
- $\epsilon$-greedy policy: that with a certain $\epsilon$ probability performs a random action otherwise it performs the best one $\to$ [[Stochastic Markov Decision process]]

The environment also has to satisfy the [[Markov property]].
### Taxonomy

To talk about reinforcement learning techniques we have to define a bunch of taxonomy. We say that a technique is **model-free** if to get the result we try to learn the solution, without computing the model, in **model-based** we want to calculate a model that then will compute the solution. 

We also define an **on-policy** algorithm to be the one that tries to approximate value functions on quantities that are associated to the policy that is used to collect the data, **off-policy** try to approximate other value functions. 

Another big distinction is whether they are **online** or **offline**, so they work data collected in real-time or on data that is already collected.

Then there is the distinction between **tabular** and **functional approximation**. In the former is where the state space is small and thus can be represented with a table, but if the number of state is very large we need some function to describe our model. This model could be [[Neural networks]] for example.

The main distinction is between **value-based**, **policy-based** and **actor-critic**. In the first we try to estimate the value function, the second we try to estimate the optimal policy. Lastly actor-critic is the best of both worlds.
### Model-free prediction

The objective is to estimate the value function of an **unknown MRP**, so a MDP plus a policy. There are a lot of approaches to solve this problem, we will only see
- [[Monte Carlo reinforcement learning]]
- Temporal Difference reinforcement learning
- Comparison between MC and TD
- $TD(\lambda)$
### Model-free control

We want to optimize the value function of an **unknown MDP**. !!! Add techniques