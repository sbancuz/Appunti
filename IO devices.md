---
tags:
  - OS
---
An [[Operating System]] should be able to communicate with peripherals, for instance even when using the keyboard or mouse. To allow communication between the main memory of the device and the outside we can use a bus. Usually we have 2 types of buses:
- Memory bus $\to$ used by the CPU to access main memory
- Port bus $\to$ it uses special addresses and instructions to communicate with outside

![[IO communication.png]]

>[!note]
>The *in* and *out* instruction in Intel CPUs are examples of such instruction. Though to call them you need special privileges.

In Linux we have 3 types of devices
- character devices $\to$ characterized by a char stream, writing has immediate impact on the device memory
- block device $\to$ memory is seen as a bunch of numbered blocks, each addressed by some number with random access.
- network device $\to$ it deal with packets of information

To access them we can just have to open them like any other file. In fact they are stored as **special files** in the file system inside `/dev/XX`. Each driver has also 2 ids to identify them. A **major** to  define the driver and a **minor** to distinguish different of the same types of devices.

>[!note]
>Only initialized drivers are present inside the `/dev/` directory. This is managed by the **sysFS** subsystem.

![[device drivers.png]]
### Communication

To communicate using Port I/O we use **device registers**, these are a special type of registers that are **memory mapped**  in order to read/write data to the peripheral memory.

>[!example]
>Legacy x86 CPUs have the UART port mapped starting form the address `0x2f8`, so to read a char from the connected device we just need 
>```nasm
>  in RBR, %al            ;; RBR = 0x2f8
>```

Memory mapped I/O isn't obviously limited by assembly instructions. So we can write from any high level language provided that we can read/write to the right addresses as if they were part of normal memory. Doing this way has also the advantage of being more efficient.

Ok, we know how to interact with the device, but how can we actually communicate with it? One simple way is to continuously **poll** the device until we receive something. This is of course very wasteful. The better way to do this is with [[Interrupts]]. So the OS will issue a request for the device and put the relevant process to sleep. Only once we have received a **hardware interrupt** from the device we will jump to the **interrupt service routine** and wake up the process to handle the response.

![[interrupts.png]]

However there is a case where polling is the better answer: when we have lots of incoming traffic that will generate a huge number of interrupts-- more than $1/\mu s$. Too many interrupts would cause a state of **live-lock** in which the CPU is in a state where it can't move forward with any user-level process because it's too busy and can't keep up. This is not so far-fetched, Gigabit internet ports can cause these problems due to the massive amount of packet they can receive.
#### DMA

Another method to resolve this issue is to introduce a new device that will sit in-between the CPU and the device and it's only purpose is to handle all the I/O while leaving the CPU free. 

![[DAM.png]]

This concept is so important today that devices are allowed to have their own dedicated DMA controllers. These are called **first party**.
### Device connection

Before reading and writing data to peripheral registers, linux drivers need to request access to devices, and they do this through `request_region` and `request_mem_region`., the first to access the I/O port space and the secondo to do memory‐mapped I/O.
Once we have the connection we can read and write with `INB` and `OUTB` respectively. 

In the case of memory mapped IO, there is an additional step because the addresses of peripherals must be mapped in the virtual address space in an **uncacheable** region and we use `IOREMAP`  before any I/O operations.

>[!note]
There exist a way to abstract between port io and mmio. You can use the generic `ioread`/`iowrite` that work the same. However, before using this with device ports, you must issue an `ioportmap` call.
### I/O scheduling

In Linux there are various schedulers for handling interrupts:
- Noop: recommended for SSDs, SANs and other flash‐based storage devices where there are no mechanical parts
- BFQ (Budget Fair Queuing): BFQ divides disk bandwidth equally among all running processes.
- Kyber: This is a simple, low‐overhead scheduler that prioritizes reads over writes. It allows to handle precise latencies.
- MQ‐Deadline: Prioritizes read operations over write operations considering their deadlines.
### Device Model

Since the Linux kernel has to run on many different architectures, how does it handle all of this diversity whilst limiting the rewriting of code? It uses a device model that abstracts the hardware by implementing an interface, so a driver must include
- Driver representation $\to$ to create coherent hierarchy of devices and sub-devices
- Device binding $\to$ to enable automatic matching and binding of the device, this simplifies the initialization and dynamic loading
- Power management $\to$ to provide a standard approach to deal with power management
- Hot plugging $\to$ to support dynamic loading of the driver
- SysFS interface $\to$ to expose the device driver to user-space using SysFS
- Event notification $\to$ to notify the user about events relative to the device

This information is mostly stored inside the `struct device`, `struct device_driver` and `struct bus_type`. To handle specific bus types both `device` and `device_drivers` can be extended accordingly. To help in developing a new driver we can use **frameworks** to streamline the process.

![[driver frameworks.png]]