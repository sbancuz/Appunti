---
tags:
  - OS
---
When booting, the [[Operating System|OS]] must know:
1) Which devices are already present on the host
2) How many interrupts are managers
3) How many processors there are

PCI are not enough to find and configure everything in a platform. So $2$ standards have been developed to provide the kernel with all the data of a platform
- ACPI $\to$ used of general purpose platforms
- Device trees $\to$ used mainly for embedded since are easier to handle for a single company
### ACPI

This is a standard developed by Intel that set a universal standard for [[Power management]] and configuration across diverse platforms and operating systems. It offers standards for detecting and initializing system components and, more importantly, it allows for a single binary kernel to operate on multiple platforms, removing the need for platform specific binaries.

![[ACPI.png]]

The kernel receives from the BIOS (or UEFI) some tables and registers. The tables contain static data structures that describe the HW component, like power events and system capabilities. ACPI registers on the other hand, are used for control tasks like initiating sleep states or interfacing with the OS via ports. 

To provide and abstraction to ACPI we have a driver that can read these tables and dynamically configure the system using AML. This AML code is stored in the **Differentiated System Description Table (DSDT)**. 

> More details about ACPI are in [[Power management]].
### Device trees

A device tree is a data structure that provides a way to describe the hardware components of a system. This description is necessary in environments where the hardware may not be able to be dynamically discovered or probed by the operating system at boot time. 

They describe various aspects of the hardware, such as what peripheral devices are present, their memory addresses, clock information and so on. This device tree is maintained in two formats:
- clear text (`.dts`) that a human can read and edit
- binary format (`.dtb`) that is the compiled version that's way easier to parse for the CPU
### Booting techniques

Booting involves various software components and mechanisms that help initialize hardware and load the operating system into memory. Both general‐purpose PCs and embedded systems have their own booting mechanisms, though there are similarities in how they prepare the system for running the OS.

In the realm of general‐purpose PCs, which typically include desktops and laptops, the booting process has traditionally been handled by two main types of firmware interfaces: 
- BIOS  
	Older firmware interface. is limited by design and slower to boot
- [[UEFI]]
	More modern alternative that addresses many of the limitations of BIOS
Embedded systems have different mechanisms for booting, often tailored to the hardware and software they run. **UBOOT** is a popular bootloader in the world of embedded Linux systems.
Bare metal operating systems, which run directly on the hardware without an underlying general purpose operating system, have simpler bootloaders if any. 

>See also: [[CPU multiplexing#Bootstrap]]