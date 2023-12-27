---
tags:
  - artificial_intelligence
---
A CSP search algorithm takes advantage of the structure of the states to create a **general** heuristic to enable the solution of complex problems. The main idea is to eliminate large portions of the search space all at once by identifying variable/value combinations that violate some [[Model optimization problems#Constraints]].

Exploiting the structure of the states means that I can modify the branching factor depending on the action that -- by looking at the failures as soon as possible -- I'm taking, thus greatly diminishing the search space and improving performance.

Each CSP has:
- A set $X$ of variables with associated set of $D$ domains
- A set of $C$ constraints that involves a subset of variables and specifies combinations of their values.

A solution can be **complete** if all variables are assigned a value and **consistent** if all the constraints are satisfied.