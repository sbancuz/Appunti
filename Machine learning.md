---
tags:
  - artificial_intelligence
---
Machine learning is an area of Artificial intelligence focused on building algorithms capable of learning, **extracting** knowledge from experience. These algorithms cannot **create** knowledge. The goal is to build programs that can make informed decisions on new unseen data.

![[Machine learning.png]]

Suppose we have the experience we collected encoded as data
$$
D=x_{1},\dots ,x_{n}
$$
#### Supervised learning

Given a set of desired outputs it learns to produce the correct output for a new set of unseen data

When the target values are real values, we have a regression problem, when they are discrete we have a classification problem.
A simple method for finding a good regression solution is through the use of a [[Perceptron]] 
#### Unsupervised learning

Exploits regularities in $D$ to build a representation for reasoning or prediction.
--> [[9. Data Mining]]
#### Reinforcement learning

It performs actions that affect the environment, and receiving rewards it learn to maximize its long-term reward.
The agent needs to compute an action-value function mapping state-action pairs to expected payoffs
$$
Q(a_{t}, s_{t}) = payoff
$$
or state-value functions mapping to expected payoffs.
$$
V( s_{t}) = payoff
$$
Reinforcement learning assumes $Q(\dots)$ to be represented as a table, but in the real world we cannot afford to compute it exactly.

##### Action selection & policy

At each time step, the agent must decide what action to take. And at any given point in time the policy $\pi(st)$ select that very action. So the policy determines how actions map to the new states, and they can be:
- deterministic : this can be modeled as a functions $\pi: S \to A$ 
- stochastic : it maps the probability distribution over the actions $\pi : S,A \to R$

> [!Warning] Exploration-Exploitation dilemma
> 
To obtain a lot of reward, the agent must prefer actions that it has tried in the past and found to lead to high payoff however, to discover such action, it has to try actions that has not selected before. So there needs to be a trade-off between the exploration of new actions and the exploitation of promising ones.

The 2 main type of policies are:
- Greedy policy: that deterministically selects an action with maximal value.
- $\epsilon$-greedy policy: that with a certain $\epsilon$ probability performs a random action otherwise it performs the best one

The environment also has to satisfy the [[Markov property]].

Since the agent has to maximize the reward it receives in the long run
$$
G_{t} \to \infty
$$
so we provide an upper bound to the payoff introducing a discount factor to the future rewards
$$
G_{t} \dot{=} R_{t+1} + \gamma R_{t+2}+ \gamma^{2} R_{t+3}+ \dots + \gamma^{k-1} R_{t+k} + \dots < \infty
$$
Thus the expected reward is defined as
$$
\mathbb  E [G_{k}] = \mathbb E \left[ \sum_{k}^{\infty}\gamma^{k}R_{t+k+1} \right]≤ R_{max} \frac{1}{1-\gamma}
$$
##### Goal and rewards

The action value function and state value function can both be decomposed as the sum of immediate reward
$$
\begin{align}
V(s) &= \mathbb E[r_{t+1} + \gamma V(s_{t+1})|s_{t}= s]  \\
Q(s,a) &= \mathbb E[r_{t+1} + \gamma V(s_{t+1})|s_{t}= s, a_{t} = a] 
\end{align}
$$
At the beginning the table $Q(\dots)$ is initialized with random values, then with time it will populate with
$$
Q(s_{t},a_{t}) = Q(s_{t},a_{t}) + \beta(r_{t+1}+ \gamma \max_{a\in A} Q(s_{t+1},a) - Q(s_{t},a_{t})) 
$$
where $\beta$ is the learning rate.