---
tags:
  - OS
---
In Linux interrupts are used by the CPU to manage hardware devices, they signal some work that must be done in order to receive some external input. 

![[IRQ.png]]

Each interrupt has a number associated with it, called the **vector**. In x86 we also have a Interrupt Descriptor Table that contains handler for all the vectors. These handlers contain pointers to the actual IRQ routine. When handling an interrupts all other interrupts are disabled, then upon invoking the routine we will disable only the current interrupt and re-enables all the other ones. Once finished we re-enable also the current one. To create an handler we can write 

```c
static irqreturn_t handler(int irq, void *mydata) {
	...
	// acquire locks on shared data
	// read/write from peripherals through MMIO
	// defer work
	// release lock
	return IRQ_HANDLED;
}
static int __init mydriver_init_module(void) {
	// allocate space for mydata
	ret = request_irq(irqnum, handler, flags, mydata);
	...
}
```

**Deferring work** means that we move the non-critical part of the handler to a later time, this improves the performance of the driver since  we can handle interrupts faster. Then, when the CPU has time it can handle all the deferred work at once. To defer work we can use the `softIRQ` API.

**SoftIRQ** are categorized according to the subsystem that will use them. They are statically allocated at compile time and are composed of a single function that serves the whole subsystem. Even though they are deferred at a later time, they will still run in interrupt context, so they preserve the atomic context of the interrupt. If there isn’t much deferred work to deal with, option one will suffice. However, if SoftIRQs start piling up and become excessive in number, the kernel initiates a group of kernel threads known as `ksoftirqd`’. These threads take on the role of invoking later on all deferred work that has not bee in finished.

To schedule softIRQs more easily we can just use **tasklets**, this is an API that exposes a one-shot deferral scheme. If our tasklet has to do some blocking work, it has to submit it to a kernel worker thread. 