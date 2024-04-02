---
tags:
  - eecs-370
---
Relevant Classes: [[EECS 370]]

Sequential Logic allows us to create circuits that "remember" or have a memory.

## SR Latch


## D Latch

A D-Latch is a Latch that is connected to a clock that "updates" while the clock is high and "holds" the last value while the clock is low.

## D Flip-Flop

A D Flip-Flop is used more often and, only when the clock goes from high to low (or low to high, or both, depending on the implementation) does it update the "stored" value to whatever the input value was at that instant. This can lead to unspecified behavior if the value of both the input and the Flip-Flop change at the same time.

The benefit, however, is for input-output loops, where the input to the data depends on the previous output for the data (and often some math in between). In the D Latch case, this can lead to a huge amount of loops / cycles, which would cause the value to become unstable (because it keeps changing). Think of the `PC + 1` case. You could be adding 1 a ridiculous number of times, because you keep doing it while the clock is high.

A D Flip-Flop fixes that, because the value is only updated once every clock cycle, so there is no unspecified behavior like above.

Sometimes, a Flip-Flop will have even an enable bit to avoid changing a value until it something else is complete (cough cough [[LC2K Multi-Cycle Datapath]])