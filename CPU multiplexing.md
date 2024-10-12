---
tags:
  - OS
---
CPU multiplexing is a technique used to maximize resource utilization by running stuff [[Kernel Concurrency|concurrently]]. This works by **context switching** to another process while the current one is idling, e.g. waiting for a keystroke. This allows other programs to execute concurrently. Of course just waiting till a process is idle isn't a great idea, it could easily happen that a process will hog all resources and never go to sleep, and other processes won't ever progress, so we introduce **time quantums**. 

![[time quantums.png]]

By multiplexing the CPU we can reduce latency significantly. Instead of waiting for a process to finish the kernel will allocate fixed time quantums and execute them in order. When a slice finished, the kernel will interrupt the [[process]] and resume with the next one. 

The kernel uses the [[Process]] control blocks to correctly perform **context switching**, i.e. pause the execution of a [[process]] and resume another one. This is achieved by saving and loading a [[process]] context onto the CPU registers.

![[context switch.png]]
### Task

In Linux a task is a common factor between [[Threads]] and a [[Process]]. A thread group, composed of multiple threads sharing a common user-mode address space but having separate stacks and program counters. Each thread represents a task that performs specific activities within the shared address space. A Unix process on the other hand doesn't share its address space with others and has a unique program counter and stack.

![[task_.png]]

A task in Linux consists of a unique program counter, two stacks (one for user mode and one for kernel mode), a set of processor registers, and an address space. Threads share address spaces, making context switching between them relatively fast compared to processes. 

![[PCB.png]]

Notable addition to the **task_struct** is the **thread_info** struct, this sits at the bottom of the kernel stack and allows it to reach the task_struct. It also holds information about the preemption statistics of the thread. To create a task a process needs to call **fork** -- that invokes **sys_clone** -- and it will create a copy of the task_struct with a different PID and PPID -- the PID that called fork. Also some resources like signals won't be inherited.

>[!note] CoW
>The OS can choose to employ a Copy on Write policy that allocates the new task_struct only when it's accessed and written to. Threads won't ever use this optimization.
### Bootstrap

This is the bootstrap procedure of the Linux kernel, it first calls the start_kernel function, then once it finishes setting the up with the appropriate architecture specific code, it starts the kernel on a new kernel thread. The PID $0$ will remain in idle for the rest of the time, only waking up only when the scheduler assigns it tasks or interrupts need to be handled.

![[bootstrap.png]]

The kernel_init function is responsible for loading the initial RAM disk image using initrd_load, providing essential modules and commands required by the user space. The init task initializes **long‐running services**, mounts hard drives, performs system cleanups, and
more. Historically, there have been several implementations of the init task. Notably, the traditional System V init and the more modern SystemD.
**System V** organizes system startups into run levels and reads from the */etc/inittab* file to decide which processes need to be initiated on a
run‐level switch. The entries in */etc/inittab* follow a format: *id:rl:action:command.* This defines what action to take and which command to run when entering a specific run level. **SystemD** in contrast provides a more efficient alternative, it organizes everything in units that need to be run, encoding in them dependencies. This allows SystemD to create a call graph in a declarative manner.
### Task scheduling

A context switch occurs when a user space program needs to enter kernel space, be it from an interrupt or a syscall. 

![[task context switch.png]]

The decision of **what** to schedule is given solely to the kernel and by which scheduling policy it follows. In deciding what to run next, it should balance
- Fairness $\to$ don't starve processes
- Throughput $\to$ overall good performance
- Efficiency $\to$ minimize overheads of scheduling
- Priority $\to$ reflect relative importance of processes
- Deadlines $\to$ respect time boundaries

Of course there is no optimal policy for every occasion, some of these goals are in conflict: deadlines vs fairness. The solution of what to use will depend on the requirements of the OS, i.e. [[General purpose OS]] or [[RTOS]].

![[Scheduling techniques.png]]

Each of these types of schedulers is called a **scheduling class**, it's essentially an API that implements how the kernel should allocate resources. All processes have a **priority** $\pi$, $\in [0, 99]$ for real time and $\in [100, 139]$ to others. In case of a non-real time process there is also a $\nu$ **nice-value** $\in [-20, 19]$. This is also referred to as **static priority**. 

To schedule the execution of tasks, the kernel employs a wait queue to hold the task until their execution, typically they enter with a **wait_event** or **wait_uninterruptible**. When waking up *func* gets called changing their state to TASK_RUNNING 

![[Wait queue.png]]

There exist also another distinction between tasks: whether they ar exclusive or not. Only one **exclusive** task of a group can be woken up at the same time, this is to resolve the Thundering Herd problem.  In addition to the wait queue there is also a **run queue** that is used to queue process that are TASK_RUNNING. 

![[run queue.png]]

Each CPU has it's own run queue which minimized contention over task selection, inside we have also queue with different scheduling policies that are selected by the **sched_class** of the task.
#### Fair scheduling

The completely fair scheduler or **CFS** emerged out of frustration with the original $O(1)$ scheduler. This had a rigid design that forced developers to make harsh choices about timeslices and priorities. For example low priority compute intensive tasks suffered a lot from constant context switching. CFS assigns timeslices dynamically based on the system load, this helps to balance CPU and I/O bound processes. For each process $p$ its time slice is computed as
$$
\tau_{p} = f(\nu_{0}, \dots, \nu_{n-1}, \hat{\tau}, \mu) \sim \max\left( \frac{\lambda_{p}\hat{\tau}}{\sum \lambda_{i}}, \mu \right)
$$
where $\hat{\tau}$ is the **latency** and $\mu$ is the **granularity**. $\lambda = k \times b^{-\nu_{i}}$ is the **weight** associated with each process. The CFS also introduces the **vruntime** variable $\rho$ that measure the dynamic priority of each process, this depends on the time $\epsilon = \frac{1}{\lambda}$ that a process has consumed.
$$
\forall {p, \Delta_{\rho_{p}}} = {\frac{\tau_{p}}{\lambda_{p}}} 
$$
However, CFS isn’t perfect and sometimes relies on unstable heuristics. CFS aims for fairness but doesn’t account for latency requirements well. Some processes need quick access to the CPU but don’t require much time. CFS doesn’t offer a way to express these latency needs. Realtime scheduling classes could handle this, but they are privileged and can disrupt other processes. Hence, the need for improvement.
### CGroups

>[!example]
>Assume user A with $2$ threads and user B with $98$ threads. User A will be given only $2$% of the time (not good!). Each user should get an equal share of the CPU, and this share is then divided among the user’s threads.

The CFS doesn't fully optimize CPU usage. We aim for each user to receive an equal share of the CPU. To implement such fairness we implements task groups that act as tasks to divide the timeslices from the parent task to their users.

![[Cgroups.png]]
### Load balancing

When you have a multi-core system, making all CPUs do equal work while respecting relative weights can be hard. We define $\gamma_{i,q}$ as the CPU usage of process $i$ on a run-queue $q$ and balance on the **total weighted load** 
$$
\Omega_{p} = \sum_{i} \lambda_{i,q} \times \gamma_{i,q}
$$
This also requires awareness of the hierarchical layout of processor cores, caches, and memory because moving a task from a CPU to another involves moving all the data that's cached, and that is slow. So we can define **scheduling domains** that create a sort of priority to where to move the data in case of a switch. The higher the slower it will be.

![[sched domains.png]]