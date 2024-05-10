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
We now define the **Bellman operator** for $V^{\pi }$ as $T^{\pi}: \mathbb R^{|S|} \to \mathbb R^{|S|}$ 
$$
T^{\pi}V^{\pi} = V^{\pi}
$$
### Optimal policy

Value function define a partial ordering over policies 
$$
\pi \geq \pi' if V^{\pi }(s) \geq V^{\pi'}(s), \forall {s \in S}  {} 
$$
For any MDP there exists **an optimal policy** $\pi^{*}$ that is better than or equal to all other policies 
$$
\pi^{*} \geq \pi \qquad \forall {\pi}  {} 
$$
This is given by maximizing the over $Q^{*}(s,a)$

This operator is 
- Monotonic $\to$ if $f_{1} \leq f_{2}\implies T^{\pi}f_{1} \leq T^{\pi}f_{2}$
- Max norm contraption $\to$ $||T^{\pi} f_{1} -T^{\pi}f_{2}||_{\infty} \leq \gamma||f_{1} -f_{2}||_{\infty}$
- $\lim_{ k \to \infty } {(T^{\pi})^{k}f = V^{\pi}}$
### Solving MDP

Solving a Markov Decision Process means to find an **optimal policy**. A naive way to do this would be 
1) Enumerate all  the deterministic Markov policies
2) Evaluate each policy
3) return the best one

The problem here is that the number of policies is exponential $|\mathcal A|^{|S|}$. So this approach will never work. A better approach would be to restrict the **policy space** and then try to use **optimization** algorithms like [[Gradient descent]] or some stochastic version if need be.

A better and more used approach is to use [[Dynamic programming]]. We have two approaches using dynamic programming.

The first is **policy iteration**. With this the iteration is divided in two steps:
1) Policy evaluation
	For a given policy $\pi$, compute the **state-value function** $V^{\pi}$ using the [[#Bellman expectation equation]]

2) Policy improvement
	Consider a deterministic policy $\pi$, would it be **better** an action $a \neq \pi(s)$? We can improve this policy by 
$$
\pi'(s) = \text{argmax}_{a}Q^{\pi}(s,a)
$$
	This improves the value for any state $s$ over one step
$$
Q^{\pi}(s, \pi'(s)) = max Q^{\pi}(s, a) \geq Q^{\pi}(s, \pi(s)) = V^{\pi} 
$$
	This means that we will always be able to find some new state-value function that will be at-worst the same, or $V^{\pi'}\geq V^{\pi}$.
	Now the question is: does policy evaluation need to **converge** to a $V^{\pi}$ or should we introduce a stopping condition after $\epsilon$ steps? One can improve after every iteration and still converge. So it does not matter, it just changes the speed, but it's unclear about this.

The other is **value iteration**. This time to find the optimal policy $\pi$ we use an iterative application of the **Bellman optimality backup** 
$$
V_{1} \to V_{2} \to \dots \to V^{*}
$$
using synchronous backups, this means: for each iterations $k + 1$, update $V_{k+1}(s)$ from $V_{k}(s)$ for every $s \in S$

>[!note]
>We do not use any specific policy, in fact some actions may not even correspond to a policy all together

Value iteration converges to the optimal state-value function, this means that
$$
||V_{i + 1} - V_{i}|| _{\infty} < \epsilon \implies || V_{i + 1} - V^{*} || < \frac{2\epsilon\gamma}{1 - \gamma}
$$
![[policy rl.png]]

Using [[Dynamic programming]] the [[Complexity of an algorithm]] becomes polynomial in the number of states, the problem now is that there are a LOT of states. 

An alternative that is faster in the worst case, but slower in the average is case is to use [[Linear programming]] to find the optimal policy, in fact we can express this problem as
$$
\begin{align}
 & \min_{V} \sum \mu(s)V(s) \\
 & \text{ s.t.} \quad V(s) \geq R(s, a) + \sum P(s'|s, a)V(s')  
\end{align}
$$

