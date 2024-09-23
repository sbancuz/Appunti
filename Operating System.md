---
tags:
  - OS
aliases:
  - OS
---
The **Operating System** is a program that acts as an intermediate layer between applications and the hardware. It's built for:
- Resource management between multiple applications
- Isolation and protection
- Portability of both applications and itself

The OS serves as a **mediator** between the hardware and the application using it. It's who decides how to manage resources efficiently, to the context of an OS resources are CPU allocations ([[CPU multiplexing]]), memory ([[Virtual memory]]), I/O and time. Another responsibility of the OS is **isolation**, i.e. all running applications are to be protected from other applications, for example if one application crashes, it will not bring down everything else.

![[OS separation.png]]

To achieve this isolation the OS will act as a **resource manager** allowing programs to run as if they are running on bare metal with unlimited resources. This makes sure that resources can be divided fairly between all processes since they are given only from one single manager. 
### Portability of applications

OS'es are implemented using the **facade pattern** to hide the complexity of dealing with many different hardware resources at the same time. This provides an, *hopefully*, stable API that a program can interface. This API comes in the form of **syscall**. They act as library calls, but into a more privileged kernel code. In Linux to call them we just refer to them by their ids, setup the call stack and call an interrupt.

>[!quote]
>Breaking user programs simply isn’t acceptable. (...) We know that people use old binaries for
>years and years, and that making a new release doesn’t mean that you can just throw that out.
>You can trust us. — Linus Torvalds

These abstractions hide the complexity of hardware interactions from applications, following the facade pattern. This allows the same applications to function across different physical resources, enabling old applications to work on new systems without modification.

>[!example]
>For example, the printf function works consistently across old and virtual terminals. The fread
and fwrite functions operate uniformly over SSDs and mechanical drives. Even device I/O is
simplified; accessing different serial peripherals can be done through file operations, such as cat
/dev/ttyS0 or cat /dev/uart.
### Extensibility

Abstractions are used everywhere in OS development, they are used to:
- create uniform interfaces from layer to layer to improve **re-usability** of code, e.g. for device drivers
- **hide complexity** associated to variants using the bridge pattern (Only define behaviors using interfaces)

![[bridge pattern is OS.png]]

Portable OS use abstract interface layers. This enables programs to interact only with standard interface components, regardless of their implementation. So, compile-time bindings between abstractions and implementations should be avoided so that they can be selected at **runtime** -- imagine having to compile the kernel for every combination of components and even when inserting a USB. This pattern is pivotal in organizing monolithic code with multiple variants of functionality, ensuring that both part can evolve independently.

>[!example]
>A real‐world example is the object‐oriented approach used in Linux’s Virtual File System. It allows the
same path resolution mechanisms to work across various file system implementations. This helps
maintain a uniform interface and manage complexity seamlessly, making the system modular and
extendable.
### Design

The design of an operating system can follow an hybrid of different architectural approaches
- No OS
	You have specific requirements and you are running a single-purpose applications because it avoids overhead of unnecessary processes and services. This is only suitable for micro-controllers
	
- Monolithic with modules
	Provided with a single large kernel binary that contain all the device drivers and systems. Examples include Linux and various BSD systems. Their advantage is that they are tightly coupled, so it results in faster performance since there are fewer layers of abstractions involved. However they can quickly become big and complex, which can affect security -- large footprint. They can also be too general, leading to slower performance.
	
	The usage of modules allows for some additional services to the implemented as external modules that can be dynamically linked with the kernel when needed without requiring system reboot. This offers more flexibility, from just a monolithic approach. 
	 
- Micro-kernel
	Here only the essential components -- not even the filesystem -- are present in the kernel. All the other things are implemented as user space processes. The setup is more resilient to system crashes since they are not part of kernel. To use these components the OS will provide some message passing functionality. Some examples are GNU Hurd or MINIX.
	
	These types of systems are typically easier maintain since they can use standard debugging tools for developing modules and they can even have independent release schedules. Stability and security are also enhanced since there is less code in general. However they have a larger memory footprint and can be trickier to debug since you have to follow messages around.
	 
- Hybrid
	They are similar to micro kernels, but some additional modules are still in kernel space to improve performance. All drivers are in user space though. These are how Windows and MacOS are made.
	
- Library Os
	Services such as networking are provided in the form of libraries and compiled with the application and configuration code