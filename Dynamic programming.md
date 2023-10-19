---
tags:
  - parallel_computing
---
The term dynamic programming was originally used in the 40's by Richard Bellman to describe the process of solving problems where one needs to find the best decisions one after another. 
Dynamic stands for the time-varying aspect of the problems, and because it sounded cool.

It's a way to solve divide and conquer problems.
One example of such algorithms is the [[Longest common subsequence]].
### Optimal substructure

An optimal solution to a problem contains the optimal solutions to sub-problems.
### Overlapping subproblems

A recursive solution contains a small number of distinct subproblems repeated many times.
### Memoization

After computing a solution to a subproblem, store it in a table. Subsequent calls check the table to avoid redoing work.