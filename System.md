---
tags:
  - mida
---
A system is a representation that exhibits the same behavior, or close, of a problem. A system can be either:
- Static
- Dynamic
### Static systems

A system from which the **input** is sufficient to predict the **output**. [[Machine learning]] deals with this exact problems.

>[!example]-
>![[static sys exa.png]]
### Dynamic systems

In dynamic systems the output will depend from both the **input** and the **time**. Time description can be either **continuous** or **discrete**.
This type of problem can also be called a **regression** problem.

>[!example]-
>![[dynamic sys exa.png]]

When dealing with time we have to differentiate the 2 cases in order to model the problem:
- Continuous $\to$ [[Equazioni differenziali ordinarie|EDO]]
- Discrete $\to$ [[Difference equation]]

When dealing with discrete functions is clear that the $y(t)$ depends on its past values. We still wish to learn a function $f$, so that $y(t) = f(\phi(t))$ but now $\phi(t)$ may contain past samples of both inputs and outputs.