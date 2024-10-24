---
tags:
  - OS
---
Unlike user‐space programs, the kernel handles interrupt processing, spinning waits, and reentrant code. These mechanisms are rarely needed in user‐space applications, where you typically don’t manage asynchronous events like interrupts or use spinning waits.

**Deadlocks** in the kernel can lead to system freezes or crashes, making their prevention essential. Additionally, the kernel must maintain high performance because any slowdown affects the entire system’s responsiveness. To achieve this we can either:
- Use lock free designs
- Use some blocking primitives that can be compiled to some platform specific implementations


