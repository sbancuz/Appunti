---
tags:
  - parallel_computing
---
Posix threads is a library that implements a [[Shared memory model]] parallel programming model with [[Threads]].

The pthreads API provides architecture for handling:
- Thread management
- [[Synchronization]]
### Thread creation

Once created, thread are like peers, and may create other threads without any implied hierarchy or dependency between them.
```c
int pthread_create(pthread_t * thread, // Indentifier of the new thread
				   const pthread_attr_t * attr, // Joinable/detached, scheduling, stack
				   void * (* start_routine) (void *), // Actual C routine to call
				   void *arg // Arguments passed to the start_routine
				   )
```
### Thread termination

A thread terminates either when:
- it returns from its starting routine
- the thread calls the `pthread_exit`
- the thread is cancelled by another thread via `pthread_cancel`
- the entire process is terminated

> [!warning]
> Created threads survive if the main calls `pthread_exit`
### Thread joining

This is a blocking procedure that halts the caller until it receives the result from the thread
```c
int pthread_join(pthread_t thread, // Identifier of the thread
				 void ** retval)   // return value of the procedure
```
The value for `retval` is provided by `pthread_exit` 

![[pthread join.png]]
### Thread detachment

A detached thread is one such thread that won't ever return it's value, so it wont ever be joined, and upon the completion of its work all the resources will be automatically collected by the OS.
### Thread barriers

Thread [[Synchronization#Barriers]] make `pthread_join` wait for other threads to reach the barrier and then begin the execution
simultaneously.

```c
int pthread_barrier_init(pthread_barrier_t * barrier,
						 pthread_barrierattr_t * attr,
						 unsigned int count) // Number of threads that have to wait
						 
int pthread_barrier_wait(pthread_barrier_t * barrier)
```
### [[Synchronization#Mutex]]

```c
int pthread_mutex_lock(pthread_mutex_t * mutex);
int pthread_mutex_trylock(pthread_mutex_t * mutex); // Non blocking lock if it fails
int pthread_mutex_unlock(pthread_mutex_t * mutex);
```
### [[Synchronization#Condition variables]]

Condition variable are a means of synchronization by explicitly signaling the meeting of a certain condition of the code.

```c
int pthread_cond_wait(pthread_condition_t * condition,
					  pthread_mutex_t * mutex)
int pthread_cond_signal(pthread_condition_t * condition)
int pthread_cond_broadcast(pthread_condition_t * condition)
```
