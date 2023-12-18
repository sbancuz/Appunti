---
tags:
  - parallel_computing
---
Halide is a Domain Specific Language embedded in C++ capable of pipelining code either at the compilation step or just in time. It's main purpose is in image processing pipelines.

![[halide.png]]
### Limitations
- All computations are over regular grids
- Only feed forward pipelines
- Bounded depth recursion
- Manually scheduled
### Scheduling

Scheduling describes how the order of the computation of the result. This can have huge impact on data locality.

>[!example]
>Think of doing for x for y or for y for x when iterating a matrix. [Other examples](https://www.youtube.com/watch?time_continue=14&v=3uiEyEKji0M&feature=emb_logo)

In Halide the default schedule is to inline producer into consumers using:
- realize -> JIT compile and execute
- Func -> pure functions
- Var -> abstract variable usable in Func
- Expr -> algebraic expressions
- Image -> in/out

>[!info]
>Loops are implicit

The basic Halide schedules are:
- Serial -> `for c: for y: for x: do(...) = ...`
- Parallel -> `for c: parallel y: for x: do(...) = ...`
- Vectorize -> `for c: parallel y: for x: vectorized x.v in [0,7]: do(...) = ...`
- Unroll -> `for c: parallel y: for x: unrolled x.v in [0,3]: do(...) = ...`
- Split -> `for c: for y_o: for y_i in [0,63]: for x: do(...) = ...`
- Reorder

>[!tip]
>There is also an auto-scheduler that tries to suggest a reasonable schedule by creating a C++ source file, this is usually used as a starting point for optimizations

