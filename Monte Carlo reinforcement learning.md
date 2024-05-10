---
tags:
  - machine_learning
---
We use the [[Monte Carlo algorithm]] to learn directly from episode of experience, no need for bootstrapping. This approach is **model free** and is based on a very simple idea: the value is equal to the mean return. So as input we get some $\{ s_{1},a_{1},\dots,s_{T} \}$ generate by following some policy $\pi$ and as output we will get a value function $V^{\pi}$

Recall that the **return** is the total discounted reward
$$
v_{t} = r_{t + 1} + r_{t + 2}\gamma + \dots + r_{t + T}\gamma^{T - 1}
$$
and that the value function is the expected return
$$
V^{\pi}(s) = \mathbb  E[v_{t}|s_{t} = s]
$$
With Monte Carlo we use the empirical mean return instead of the expected one. But we need to decide, we count multiple times the visits to a state $s$ or not? The former is **unbiased** while the latter is not. So we prefer the first visit when we have a lot of sample, if not multiple is fine.