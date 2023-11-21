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
- relative value : it's a fraction of a value, usually between  $0$ and $1$ to represent percentages
- 0-1 : this represent a logical value
- discrete value

### Rules

The rules are constraints that our system must follow. This are expressed as multi-variable inequalities
$$
x_{a}+ 2x_{b} \leq 15
$$
To transform a requirement from an inequality to an equality we can add a slack variable such that
$$
x_{a} + 2 x_{b} -x_{s} = 15
$$
and it measures how much of a given resource is still available in the system.
#### Blending constraints

There can also be blending constraints that require a certain percentage goal to a mix of variables
$$
\frac{35x_{s} + 40 x_{c} + 180 x_{p} + 100 x_{b}}{300 + \dots + 400x_{b}} \geq 30 \%
$$
though this type of constraint is not linear, but we can resolve this just by multiplying the denominator to both sides and then putting all the variables on one side of the constraint.
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
### Objective function

The objective function is used to represent the minimization or maximization of appropriate linear functions. In order to switch between the two we just
$$
max \sum c_{j}x_{j} = - min \sum (-c_{j})x_{j}
$$
>[!note]
>We don't have to change the sign of decision variables

Another type of objective function are the **bottleneck functions**, which are used either to minimize the maximum (**minimax**) or to maximize the minimum (**maxmin**). The problem is that such functions are non linear. This is resolved by adding another variable to separate the constraints of the objective functions.
$$
\begin{align}
\min \max p_{ij}x_{ij} \implies \begin{cases}
\min d \\
d \geq p_{ij}x_{ij}
\end{cases} \\
\max \min p_{ij}x_{ij} \implies \begin{cases}
\max d \\
d \leq p_{ij}x_{ij}
\end{cases}
\end{align}
$$
### Multi-criteria analysis

When there are conflicting objective functions like minimize $a$ and maximize $b$ we can get the solution by graphing all the values and getting the boundaries 

![[Frontier.png]]