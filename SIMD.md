---
tags:
  - parallel_computing
---
SIMD (Single Instruction Multiple Data) is an instruction set that operates with registers of 128, 256 and sometimes even 512 bits. They are used to parallelize execution while still using only one [[Threads]] to execute the instruction.

![[SIMD.png]]

For compilers is quite hard to decide if a code block can be vectorized to use SIMD registers.
### Loop carried dependencies

```c
void lcd_ex(float* a, float* b, size_t n, float c1, float c2) {
	for (int i = 0; i < n; i++) {
		a[i] = c1 * a[i + 17] + c2 * b[i];
	}
}
```

This loop can only be vectorized only if the vector length is less than the distance length, e.g. the 17 in the example.

>[!warning]
>Loop iteration at the beginning and end may not be vectorized.
### Implementation in CPU

There is one radical difference with respect to normal architectures, we need a central controller that sends the vector data to all the processing elements. There is only one program counter. 

![[array controller.png]]

There are $3$ variations of SIMD machines:
- [[Vector architectures]]
- SIMD extensions $\to$ SSE, AVX, MMX
- GPUs

