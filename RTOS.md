---
tags:
  - OS
---
Real time [[Operating System|OS]] generally weigh more deadlines, priority and scheduler efficiency. If the deadlines are **critical** we say that is a **Hart RT**.  When a higher priority thread becomes available, it immediately takes control without waiting for the current thread to finish, but they **assume** that high priority tasks don't occupy the CPU.