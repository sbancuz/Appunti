---
tags:
  - operations_research
---
When we need to resolve an optimization problem we have to think about:
- Decisions $\to$ Variables
- Rules $\to$ Mathematical constraints
- Objective $\to$ Functions

>[!warning]
>In this course the function MUST be linear

### Variables

Variables are used to represent decisions, and can be:
- non negative
$$
\begin{align}
x_{a} = \text{ number of } A  \\
x_{b} = \text{ number of } B 
\end{align}
$$
- unrestricted : they are used to manage perturbations to a current solution
$$
\pi_{i} = \pi_{i}^{+} - \pi_{i}^{-} \text{ where } \pi_{i}^{+},\pi_{i}^{-} \geq 0 
$$
- relative value : it's a fraction of a value
- 0-1 : this represent a logical value
- discrete value
