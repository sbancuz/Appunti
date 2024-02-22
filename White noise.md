---
tags:
  - mida
---
White noise is a sequence of **independent identically distributed** [[Probability theory#Random variables]], this means that:
- The probability distribution is identical at all times -- i.e. [[Stationary process]]
- It's independent in correlation at different times
$$
\begin{align}
\mathbb E  [v(t)]   = 0 \qquad
\gamma(\tau)  & = \begin{cases}
0  & \tau \neq 0 \\
\lambda ^{2}  & \tau = 0 \text{ Variance}
\end{cases}
\end{align}
$$
This means that white noise is **completely unpredictable**
$$
v(x) \sim \text{Wn}(0, \lambda^{2}) \qquad v(t) \sim \text{WGn} (0, \lambda^{2}) \text{ $\gets$ Gaussian }
$$
>[!example]-
>$v(t) = \eta(t) + c \eta(t-1)$ where $\eta(t) \sim \text{Wn} (0, \lambda^{2})$.
>   ^^ *This is an example of a moving average*.
>   
>   We need to check if it is a [[Stationary process]], so:
>   $$
>   \begin{align}
>\mathbb E[v(t)] &= \mathbb E[\eta(t) + c \eta(t-1)] = \mathbb E[\eta(t)] + c \mathbb E[\eta(t-1)] = 0 \\ \\
>\gamma(0) &= \text{Var}[v(t)] = \mathbb  E [(v(t) - 0)^{2}] =\mathbb E[(\eta(t) + c\eta(t-1))^{2}]\\ &= \mathbb E[\eta(t)^{2}] + c^{2} \mathbb E[\eta(n-1) ^{2}] + 2c \mathbb E[\eta(t)\eta(t-1)] = \gamma^{2} + c^{2}\gamma^{2} +2c0 \\ \\
>\gamma(t, t +1) & = \mathbb E[v(t)v(t+1)] = \mathbb E[(\eta(t) + c\eta(t-1))(\eta(t + 1) + c\eta(t))] \\ &= \mathbb E[\eta(t)\eta(t+1)] + c \mathbb E[\eta(t + 1)\eta(t-1)] + c \mathbb E[\eta(t)^{2}] c^{2} \mathbb E[\eta(t)\eta(t-1)] = c\lambda^{2}\\ \\ 
>\gamma(t, t +\tau) & = \mathbb E[v(t)v(t+\tau)] = \mathbb E[(\eta(t) + c\eta(t-1))(\eta(t + \tau) + c\eta(t + \tau - 1))] = 0\\
>\end{align}
>$$
>Our function now becomes:
>$$
>\begin{cases}
>\gamma(0) = (1+c^{2})\lambda^{2} \\
>\gamma(1) = c\lambda^{2} \\ \gamma(\tau) = 0
>\end{cases}
>$$
>So the moving average process is weakly stationary.










