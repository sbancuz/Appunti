---
tags:
  - parallel_computing
---
![[Automatic parallelization]]

![[Parallelization by hand]]
Designing a good parallel algorithm by extracting all the available parallelism is not enough, because not all is exploitable on real architecture. We need to descrive the parallelism to the compilation tools to make it exploitable.

>[!warning]
>Creating threads is expensive, sometimes the best solution is to keep it sequential

There are many tools to describe parallel algorithms, in fact many languages have been developed to tackle this issue, but not many manage to stick due to be new languages and lack of proper programming tools. For this purpose extension to existing languages have also been developed that take advantage of already mature compilers and tools to parallelize a sequential language whenever possible.  [[Parallel technologies]]
### Dependency

A dependency arises when one operation depends on an earlier operation to complete and produce a result before this later operation can be performed. We can extend this notion of dependency to resources. Two statements can execute in parallel iff there are no dependencies between them. 

When statements execution does not interfere with other we have sequential consistency. This means that the processor can execute these  statement out of order.

Given statements $S_{1}$ and $S_{2}$, :
- $S_{2}$ ha true/flow dependency on $S_{1}$ iff $S_{2}$ reads a value written by $S_{1}$ -> Read After Write
- $S_{2}$ has a anti-dependency on $S_{1}$ iff $S_{2}$ writes a value read by $S_{1}$ -> Write After Read

We can use [[Graphs]] to show the dependency of relationships of the statements.
A simple technique to remove dependency is to rename all the variables to make them unique.

Data dependency relations can be found by comparing the IN and OUT sets of each node in which
- IN(S) $\to$ set of memory locations that may be used in $S$
- OUT(S) $\to$ set of memory locations that may be modified by $S$
$$
\begin{align}
&out(S_{1}) \cap in(S_{2}) \neq \emptyset \implies& S_{1}\delta S_{2} \implies& \text{flow dependence} \\

&in(S_{1}) \cap out(S_{2}) \neq \emptyset \implies& S_{1}\delta^{-1} S_{2} \implies& \text{anti dependence} \\

&out(S_{1}) \cap out(S_{2}) \neq \emptyset \implies& S_{1}\delta^{0} S_{2} \implies& \text{output dependence}
\end{align}
$$
Significant parallelism can be identified withing loops.
```c
for(int i = 0; i < 100; i++)
	a[i] = i;
```
In this case the $i$ variable can be ignored. This is known as a DOALL loop in which:
- all iteration are independent of each other
- all statement be executed in parallel at the same time

We can prove this can be easily parallelised just by unrolling the loop into all its instructions or by splitting/merging loops depending on their overhead.
#### Loop carried dependency
```c
for(int i = 1; i < 100; i++)
	a[i] = a[i-1] + 100;
```
cannot be parallelised since the $i$-th operation depends on the $i-1$ but,
```c
for(int i = 5; i < 100; i++)
	a[i - 5] = a[i] + 100;
```
can be parallelized in clusters of $5$ elements since on the first cluster only depends on the next one. If we were to use more than $5$ elements, we'd introduce dependency since it would not be already computed and, thus, it cannot be parallelized.
### Parallel patterns

A recurring combination of task distribution and data access that solves a specific problem in parallel algorithm design. Patterns are universal - thus, can be used in any parallel programming system. 
#### Nesting pattern

Nesting is the ability to hierarchically compose patterns, this appears in both serial and parallel algorithms. This can divide each task in block that can represent different patterns.
#### Serial control patterns

This is based on extracting execution form a sequence and parallelizing them, in selection we can execute both branches and take only the one result we want depending on the condition, iteration and recursion.

>[!info]
>A tail recursion is a special recursion that can be converted into iteration, this is useful in functional programming
#### Parallel control patterns

- Fork-join: allows control flow to fork into multiple parallel flows, then rejoin later
- Map: performs a **pure** function over every element of a collection
- Stencil: **pure** function that has access to a set of neighbors (convolution)
- Reduction: combine every element in a collection using an associative combiner **pure** function
- Recurrence: loop iteration can depend on one another

#### Serial Data management patterns

- random read
- random write
- stack allocation $\to$ preserves locality, each thread has is own thread
- heap allocation $\to$ slower but can be accessed by other threads if need be
- objects