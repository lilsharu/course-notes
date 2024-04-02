---
tags:
  - eecs-370
---
Related Classes: [[EECS 370]]

When calling a function, the currently stored register values have to be saved at some step in the process—at least the ones whose values are going to be used after the function call is over. There are two ways this saving can be implemented: it can be *caller-save*, or *callee-save*.

When considering all possible programs, these roughly equate to the same performance / situation, so the only thing that's really important in the end is consistency.

## Caller Save

When using the caller-save paradigm, this means that each function itself is responsible for saving all relevant registers before calling any function (onto its stack) and then retrieving them once the task is done.

There are a few key advantages to this. Primarily, the calling function knows which values it still needs to use after the function is done, so it knows which values *don't* need to be saved.

## Callee Save

The callee-save paradigm is the opposite idea. Each function, before running or executing, assumes that the place that it was called from didn't save any registers. This means that the function will need to save and restore all the registers that it plans on using at the start and end of the function.

Again, the key advantage here is that only the registers that the function is planning on using end up needing to be saved on the stack: the rest can simply be ignored because they're not changed.

## Combining Both

What a lot of Modern ISAs do, then, is to have some registers be caller-saved registers and others be callee-saved registers. This way, the compiler can assign variables to the most optimal register to minimize stack accesses. For example, a variable that is only used before a function call would be added to a caller-save register if possible, so that by the time the function is called, you don't need to access the stack to save said value (since it wasn't relevant after the function call anyways).