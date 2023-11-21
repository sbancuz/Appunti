---
tags:
  - operations_research
---
When we want to resolve an optimization problem we have to construct a mathematical model. 
The formulation of such model implies three fundamental points:
- Decisions $\to$ Variables
- Objective to be optimize $\to$ Functions
- Definition of feasible solution using rules $\to$ Mathematical constraints

>[!warning]
>In this course the function MUST be linear

Models can be divided in three main classes:
- Mathematical programming -> the entire system is described through mathematical functions who's objective is to minimize/maximize
- Game theory -> we model mathematical behavior through players, each of whom has a fixed role and strategy
- Simulation models -> we try to reproduce reality (or a very complex system) to study its behavior

In any case, the result of a model is always an abstraction of reality and, therefore, can't represent all the details and nuances of a system needed to approach the real problem. The space of feasible solutions of a problem can be represented on a Cartesian plane by representing each constraint as a lines.

![[feasible solution.png]]

Any points belonging to the feasible region corresponds to a possible combination of the two. In order to find the best one, we have to restrict the range of research by remarking that the optimal solution must exploit at least one resource to the utmost extent. This means that our research can be limited to the edge of the feasible region space.
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

### Rules

The rules are constraints that our system must follow. This are expressed as multi-variable inequalities
$$
x_{a}+ 2x_{b} \leq 15
$$
#### Blending constraints

There can also be blending constraints that require a certain percentage goal to a mix of variables
$$
\frac{35x_{s} + 40 x_{c} + 180 x_{p} + 100 x_{b}}{300 + \dots + 400x_{b}} \geq 30 \%
$$
#### Logical constraint

Binary values can be seen as logical variables and thus can be used to express propositional operator. To use a logical constraint onto real variables we have to create systems
$$
\begin{align}
 y_{1}   = & \begin{cases}
1  &  x_{1} > 0 \\
0  & \text{otherwise}
\end{cases} \\
 y_{2}   = & \begin{cases}
1  &  x_2 > 0 \\
0  & \text{otherwise}
\end{cases} \\ 
\implies  & \begin{cases}
y_{1} + y_{2} \leq 1 \\
x_{1} \leq M y_{1} \\
x_{2} \leq M y_{2}
\end{cases}
\end{align}
$$
where $M$ is just a big constant or just a limit.
### Transformations

We can transform a rule into another equivalent rule if we need.
$$
\sum_{i} a_{i}x_{i} \leq b \implies\sum_{i} -a_{i}x_{i} \geq -b 
$$
This could be needed if the solver can't work with a certain constraint.
To transform an inequality to an equality we can just add a parameter $s \geq 0$ such that
$$
\sum_{i} a_{i}x_{i} ± s\leq b
$$
and varying the value of $s$ gives us a discriminant that tells us if our result is equal or not to $b$
### Multi-criteria analysis

When there are conflicting objective functions like minimize $a$ and maximise $b$ we can get the solution by graphing all the values and getting the boundaries 

![[Frontier.png]]