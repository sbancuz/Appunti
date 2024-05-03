---
tags:
  - machine_learning
---
A Markov Decision process is described by a tuple $\left< S,A,P,R \right>$ where $P$ is the **state transition probability matrix**. Since the agent has to maximize the reward it receives in the long run
$$
G_{t} \to \infty
$$
>[!note]
>This reward is modeled as a scalar because it's tested to be enough for the agent to learn, but this assumption, called the **Sutton assumption** could very well be wrong.

Another thing we have to consider is the time domain of our agent:
 - finite
 - indefinite -- until some conditions are met, like a checkmate
 - infinite

And most importantly **how to assign the reward**
-  sum all the rewards
- average over all rewards
- sum all the **discounted** rewards 
- mean variance

>[!note]
>We have to provide an upper bound to the payoff introducing a discount factor to the future rewards
>$$
 G_{t} \dot{=} R_{t+1} + \gamma R_{t+2}+ \gamma^{2} R_{t+3}+ \dots + \gamma^{k-1} R_{t+k} + \dots < \infty
>$$

Thus the expected reward is defined as
$$
\mathbb  E [G_{k}] = \mathbb E \left[ \sum_{k}^{\infty}\gamma^{k}R_{t+k+1} \right]≤ R_{max} \frac{1}{1-\gamma}
$$
#### Goal and rewards

The action value function and state value function can both be decomposed as the sum of immediate reward
$$
\begin{align}
V(s) &= \mathbb E[r_{t+1} + \gamma V(s_{t+1})|s_{t}= s]  \\
Q(s,a) &= \mathbb E[r_{t+1} + \gamma V(s_{t+1})|s_{t}= s, a_{t} = a] 
\end{align}
$$
At the beginning the table $Q(\dots)$ is initialized with random values, then with time it will populate with
$$
Q(s_{t+1},a_{t+1}) = (1- \beta)Q(s_{t},a_{t}) + \beta(r(s,a)+ \gamma \max_{a\in A} Q(s_{t+1},a)) 
$$
where $\beta$ is the learning rate.
