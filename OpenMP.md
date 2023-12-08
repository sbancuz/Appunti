---
tags:
  - parallel_computing
---
This is an API for multi-threaded [[Shared memory model]] programming. It provides its functionality mostly though **compiler directives** and the rest with [[#Runtime functions]].

>[!warning]
>This needs proper compiler support, even though `gcc` and `clang` support it

This library is focused mostly on ease of use, just 3 or 4 directives are enough to implement significant parallelism. This is achieved with a **fork-join** paradigm:
- a **master** forks a specified number of **slave** threads
- tasks are divided among **slaves**
- **slaves** run concurrently as the runtime environment allocates threads to different processors

![[openmp extensions.png]]

OpenMP makes use of preprocessor directives called `#pragma omp <name> [list of clause]`.
### Parallel control structures

OpenMP programs execute serially until they reach a `parallel` directive, then the executing thread will spawn a group of slave threads and becomes the master ($ID:0$). Each slave thread will execute a copy of the code in the scope then the execution will resume serially.
```rust
#pragma omp parallel <num_threads (num)> <if (condition)>
{
	// Stuff
}
```

The number of worker threads can also be imposed by the `omp_set_num_threads()` function callable from C.
### Work sharing constructs

These constructs divide the execution of a code region among the members of the team that encounters it.

>[!warning]
>All work sharing construct **must** be enclosed withing a parallel region, thus they don't create new threads

There is no implied barrier upon entry to a work sharing construct, however there is an implied barrier at the end of the work.
#### For

This construct parallelize the execution of the iterations of a for loop
```rust
#pragma omp parallel <num_threads (num)> <if (condition)>
{
	#pragma omp for <schedule> <nowait> <data-scope(...)> 
	// for loop
}
```

The most typical schedules are:
- static -> loop iterations are divided into blocks of size *chunk* and then statically assigned to threads. If the *chunk* size is not specified, the iterations are evenly divided contiguously among the threads.
- dynamic -> loop iterations are divided into blocks of size *chunk* and then dynamically assigned to the threads
- runtime -> `OMP_SCHEDULE` environment variable sets the type of schedule
#### Sections

Specifies that the enclosed sections of code are to be executed in parallel. Each section is executed once by a thread in the team.

```rust
#pragma omp parallel
{
	#pragma omp sections
	{
		#pragma omp section
		{
			/* code section 1 */
		}
		#pragma omp section
		{
			/* code section 2 */
		}
	}
}
```
#### Single-Master

These function like sections but the `single` are only accessible by **one** single thread and `master` is only accessible by the **master**
```rust
#pragma omp parallel
{
	#pragma omp single
	{
		/* code section */
	}
	#pragma omp master
	{
		/* code section */
	}
}
```
#### Tasks

The `task` directive specifies a work unit which may be executed or deferred to another thread in the same team. `taskwait` introduces a [[Synchronization#Barriers]] and `taskyield` interrupts the execution of the current task and then later it may be resumed.
```rust
#pragma omp task
{
	/* code section */
}
#pragma omp taskwait
#pragma omp taskgroup // Like taskwait but works for the child threads too
#pragma omp taskyield
```

This construct is very useful when dealing with irregular and runtime-dependent execution flows like the while loop. It can be seen as a queuing system that dynamically assigns work to threads.

Tasks can be very useful even with [[Pipeline pattern]]. By creating tasks instead of sections, each thread can execute any task as long as its inputs are ready.
```rust
	#pragma omp task depend(out: variable) { read; }
	#pragma omp task depend(in: variable) { compute; }
```

`priority(int prio)` can also be used to hint that something is more important.

>[!example]-
>![[tasks dep ex.png]]
#### Nested parallelization

OpenMP `parallel` constructs can be nested to achieve different levels of parallelism, each `parallel` region will spawn new threads per thread that enters that region
```rust
#pragma omp parallel num_threads(3)
{
	// Code executed by 3 threads
	#pragma omp parallel threads(2)
	{
		// Code executed by 3x2 = 6 threads
	}
}
```

>[!warning]
Not all system allow nested parallelization by default, check the `OMP_NESTED` variable to find out 

This technique can easily cause over-subscription of the threads which can degrade performance since the CPU has to waste a lot of cycles just context switching. In such cases setting the number of threads dynamically can improve performance. 

TLDR: use nested when the number of threads that the process will spawn its small
#### [[SIMD]] vectorization

The loop is divided into *chunks*, each chunk is executed by a single thread with a SIMD instruction and it will be easier for the compiler to generate this kind of instructions since it's the programmer's job to specify this detail

```rust
#pragma omp simd <data-scope> \
				 <collapse> \ // fuse two perfectly nested loops
				 <simdlen(size)> \ // suggest preferred vector lenght
				 <safelen(size)> // safe length for loop carried dependecies
// for loop
```

This directive can be used in conjunction with the `for` directive
```rust
#pragma omp for simd \
	<schedule(simd:static, size)> // chunk size = ceil(req/simdlen) * simdlen 
// for loop
```

Function declarations can also be declared as inlinable and vectorizable when inside a SIMD loop.
```rust
#pragma omp declare simd \ 
	<linear(var)> \ // value changes linearly from one call to another
	<uniform(var)> \ // same value for all calls
	<notinbrach/inbrach>
// function definition
```
#### Heterogeneous architectures computation

Heterogeneous architecture means that the main execution is processed by the CPU while the parallelization part can be done by accelerators like GPUs, FPGAs or DSPs.

```rust
#pragma omp target \
	<nowait> \ // Don't block execution of the main thread
	<map(type: vals,...)> // Copies varaibles that are needed to the target
						  // Default type: tofrom
{
	// code
}
```

If present the execution is offloaded to an accelerator and blocks the main thread execution until its finished, if not, it falls back on the host.

![[map types.png]]
### [[Synchronization]]

The `critical` directive specifies a region of code that must be executed by only one thread at a time.
```rust
#pragma omp critical [name]
{
	// Stuff
}
```

>[!warning]
>Names are global identifiers
#### [[Synchronization#Barriers]]

The `barrier` directive synchronizes all threads in the team. When a barrier is reached, a thread will wait for all other threads to finish their execution until the barrier.
```rust
#pragma omp barrier
```
#### [[Synchronization#Atomics]]

The `atomic` directive ensures that a specific storage location is accessed atomically. Multiple reads and writes are not allowed and is only valid for the next statement
```rust
#pragma omp atomic
```
#### Flush

OpenMP employs a **relaxed** memory consistency mode, i.e., all threads have the same view of memory at specific points in the code. In between these points each thread has its own temporary view of the memory. This is a problem when dealing with shared data writes.

The `flush` directive enforces global consistency of shared variables, this mean that between a flush and the next update of shared memory all threads will see the same values.
```rust
#pragma omp flush [flush-set] // Don't specify flush-set  if possible
```
#### Cancel

>[!warning]
>This feature was introduced in version 4.0

The `cancel` directive provides the best effort for terminate the execution of a team of threads. This is implemented with the setting of a flag with
```rust
#pragma omp cancel <construct-type>
```
and this flag is checked when invoking 
```rust
#pragma omp cancellation point
```

>[!note]
>Setting the flag also implicitly checks if it is already set and terminates
### Data environment

In OpenMP most variables are shared by default, different data scopes can be used to explicitly define how variables should be scoped
- `private (list)` -> variables in this list are private to each thread
- `shared (list)` -> variables in this list are shared among all threads and there exists only one in memory
- `default (shared | none)` -> none means that the programmer must scope all variables
- `reduction (operator: list)` clause helps to perform a reduction upon the completion of all the tasks.

>[!note]
>Available operators for the reduction are: `+ * - & | ^ && || min max`
### Runtime functions

```c
int omp_get_num_threads() // returns the number of threads in the parallel region
int omp_get_thread_num() // return the thread identifier
void omp_set_num_threads(int num_threads) // set the number of thread for the next region
double omp_get_wtime() // returns wall clock time
double omp_get_wtick() // return the number of seconds between two clock ticks
void omp_set_nested(bool nested) // set if nested parallel blocks are allowed 
void omp_set_max_active_levels(int max_levels) // set max level of nested blocks
void omp_set_dynamic() // set the number of threads dinamically
```
### Environment variables
```c
OMP_SCHEDULE
OMP_NUM_THREADS
OMP_NESTED
OMP_STACKSIZE
OMP_WAIT_POLICY
OMP_PROC_BIND
OMP_NESTED // If nested parallel blocks are allowed 
OMP_MAX_ACTIVE_LEVELS // Upper limit on the number of active parallel regions
OMP_THREAD_LIMIT 
```
