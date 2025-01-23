---
tags:
  - OS
---
When talking about power management we refer to tools and techniques to consume **as little power as possible**, give the system state, configuration and use case. So it's goals are
1) Improve reliability, so reduce the temperature and consequently power $P$
2) Improve battery lifetime and energy consumption
3) Ensure regulatory compliance

To measure power metrics we use the **Thermal Design Power** or TDP which is the average value of a physical power that a cooling system must be able to dissipate to ensure **sustained reliability**.

![[power consumption.png]]

Today, the main source of consumption is the frequency and voltage of each system device. This is defined according to the Dennard scaling, that implies that higher frequencies lead to disproportionate power demands. So the problems can be condensed to *how little of a device can i use to achieve my task?* Switching voltage is not as simple as it seems, it consumes time, energy and computational power. If not managed correctly the energy saved could be spent in the transitions. 

[[Boot#ACPI]] took a pragmatic approach and simplified it all. It provides mechanisms for putting the computer as a whole in and out of sleep. It provides tables that describe devices and their power states and exposes control over them. This means that the OS must reason on a simplified **state machine**. These states are commonly referred to as:
- G-type
	these are groups of S-type that describe, in a coarse grained way, the behavioral state of a computer system (working, appear off, off but can wake up on event, completely off)- S-type
- S-type
	these are the sleep states and are grouped in G-type states. They describe how the computer implements the G-state 
- C-type
	the CPU states specifically refer to the power management capabilities of a computer's CPU. This allows for a reduced clock speed of even shut down completely when idle in order to conserve energy
- P-type
	the performance state is a power management feature that allows the CPU to adjust its clock speed and voltage based on workload demands. These only make sense in a C$0$ configuration
- D-type
	Equivalent to C-states, but for peripheral devices

![[ACPI states.png]]
### Power management stack

Power management is divided in two parts. The **ACPI daemon** and the **OSPM**. The daemon listens for power events and manages system wide power states S and G. When the scheduler identifies, so it changes the P-state, it communicates to the **CPUFreq module** of the OSPM the desired change. This change is triggered by modifying the Performance Control Machine Register.