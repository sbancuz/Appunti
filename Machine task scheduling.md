---
tags:
  - operations_research
---
Let us pose the problem of processing $n$ tasks $1,\dots,n$ on $m$ machines denoted by $1,\dots,m$. The execution time of a task $j$ on machine $k$ is denoted as $s_{jk}$. The different machines can perform only one task at a time and each task must be brought to the end. The goal is to try to minimize the end time of the last task. 

To determine the sequence of that set the beginning time of the task $j$ on machine $k$. These variables make it easy to formulate the constraints relative to the making sequence of each task
$$
t_{jk} + s_{jk} \leq t_{jk+1}
$$
In order to properly represent the objective function we introduce a variable $T$ that will be greater than or equal to the end time of the last task on the last machine
$$
t_{jm} + s_{jm} \leq T
$$
And since we have to minimize the total time $T$ the objective function will be 
$$
	\min T
$$
To prevent that two execution from happening one the same machine simultaneously. The idea is that each pair of tasks $i$ and $j$ on each machine $k$
$$
t_{ik} + s_{ik} \leq t_{jk}
$$
or 
$$
t_{jk} + s_{jk} \leq t_{ik}
$$
To express the disjunction between the two constraints we need a logical variable $y_{ijk}$ that is $1$ if $i$ precedes $j$ on $k$ and $M$ is a value big enough to render a constraint redundant
$$
\begin{align}
t_{ik} + s_{ik} \leq t_{jk} + M(1-y_{ijk}) \\
t_{jk} + s_{jk} \leq t_{ik} + My_{ijk}
\end{align}
$$

