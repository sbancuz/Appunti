---
tags:
  - parallel_computing
---
Synchronization is a method to avoid non deterministic behavior in a multi execution environment.
### Race conditions

A race condition occurs when two threads access the same variable, and at least one of them tries to write to it. Since any operation may happen at any time it may lead to non deterministic behavior.
### Barriers

The barrier forces all the threads that are doing the parallel computation to wait until all involved threads have reached the barrier. When the threads have reached the barrier, the threads are released and begin computing together.
### Mutex

Mutex are variable that protect [[Shared memory model]] applications from data races using mutual exclusion. Only one thread can **lock** a mutex variable at any given time and if several threads try to lock a mutex, only one will be successful. If a thread cannot acquire the lock, then it will be blocked. 

>[!warning]
>Multiple mutexes can lead to deadlocks if not handled correctly

There are 3 types of mutexes:
- normal -> No deadlock detection and no errors
- error check -> No deadlock detection but it will return errors when trying to do invalid operations
- recursive -> It keeps track of how many threads try to lock and then it will unlock only when all threads have released their lock
### Condition variables

Condition variables allow threads to synchronize explicitly by signaling the meeting of some condition. Without these, the programmer would have to poll to check if this conditions are met.
### Atomics

Atomic variables are variables that can be accessed and modified in **one** operation, this means that are not susceptible to race conditions and do not require locks 