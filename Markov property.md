---
tags:
  - artificial_intelligence
---
Given a set of states, actions and rewards. The next sate $s_{t+1}$ and reward $r_{t+1}$ depend only on the current state $s_{t}$ and action $a_{t}$. So
$$
\mathbb P(X_{t + 1}=j |X_{t} = i, X_{t-1} = k_{t-1}\dots, X_{1} = k_{1}) = \mathbb P(X_{t + 1}=j |X_{t} = i)
$$
The environment can thus be modeled as a [[Markov Decision processes]] that has one-step dynamic described by a probability distribution.