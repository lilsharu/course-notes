---
tags:
  - eecs-370
---
Related Classes: [[EECS 370]]

This is the most commonly used methodology to represent signed integers in binary. Recall that in binary, the $i$-th digit from the right represents $2^i$, where $i$ starts at 0. Consider the following number: $$0b1101 = 1 \cdot 2^3 + 1 \cdot 2^2 + 0 \cdot 2^1 + 0 \cdot 2^0 = 8 + 4 + 1 = 13.$$

Two's Complement numbers are very similar: the only difference is that the most significant bit is now negative. Considering the same example, the number $0b1101$ in two's compliment is: $$0b1101 = 1 \cdot (-2^3) + 1 \cdot 2^2 + 0 \cdot 2^1 + 0 \cdot 2^0 = -8 + 4 + 1 = -3.$$
If you want to negate a number, it's very simple in two's complement: flip every bit (or `nor` a number with itself or 0) and then add 1.

So, to get the -3 above, we'd start with a binary 3: $0b0011$. Then, we'd flip all the bits to get $0b1100$. Finally, we'd add 1 to get $0b1101$, which is the same as above.

As you might be able to tell, the range of an $n$-bit two's complement number is: $[-2^{n - 1}, 2^{n - 1} - 1]$ (inclusive).