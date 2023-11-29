---
tags:
  - operations_research
---

$$
P : \text{ } \begin{aligned}
\max \text{ }&cx \\
  & Ax\leq b
\end{aligned}
\text{ } D : \text{ } \begin{aligned}
\min \text{ }&yb \\
  & y A =  c\\
  & y\geq 0
\end{aligned}
$$
Consider a pair of dual problems $P$ and $D$, now let $\dot{x}$ and $\dot{y}$ be feasible their solutions. The following properties are equivalent:
- $\dot{x}$, $\dot{y}$ are optimal
- $c\dot{x}=\dot{y}b$
- $\dot{y}(b-A\dot{x})=0$

Solutions are said to be **complementary**  if the third condition - called **complementary slackness condition** - holds. This means that the solution is optimal iff $\dot{y} \geq 0$ and it holds component by component
$$
\dot{y}_{i}(b_{i}-A_{i}\dot{x}) = 0
$$
and it further implies that
$$
\begin{align}
\dot{y}_{i}\ne0 \implies A_{i}\dot{x} = b_{i} \\
A_{i}\dot{x} \ne b_{i} \implies \dot{y}_{i} = 0
\end{align}
$$
Now given this other LP dual problem
$$
P : \text{ } \begin{aligned}
\max \text{ }&cx \\
  & Ax\leq b \\
  & x\geq 0
\end{aligned}
\text{ } D : \text{ } \begin{aligned}
\min \text{ }&yb \\
  & y A \geq  c\\
  & y\geq 0
\end{aligned}
$$
and let $\dot{x}$ and $\dot{y}$ be feasible solutions for $P$ and $D$, respectively: then $\dot{x}$ and $\dot{y}$ are optimal iff
$$
\begin{align}
\dot{y}_{i}(b_{i}-A_{i}\dot{x}) = 0 \\
(\dot{y}A^{j}-c_{j})x_{j} = 0
\end{align}
$$
and it implies that
$$
\begin{align}
\dot{y}_{i}\ne0  & \implies A_{i}\dot{x} = b_{i} \\
A_{i}\dot{x} \ne b_{i}  & \implies \dot{y}_{i} = 0 \\
\dot{x}_{j} \ne 0  & \implies (c_{j}=\dot{y}A^{j}) \\
(c_{j}\ne\dot{y}A^{j})  & \implies \dot{x}_{j} = 0
\end{align}
$$

