---
tags:
  - eecs-370
---
Related Classes: [[EECS 370]]

Floating Point Numbers are a way to represent non-integer rational numbers using binary. It takes some inspiration from scientific notation, essentially representing a number using the following form:
$$ x \cdot 2 ^ {\text{y}}.$$
This allows us to represent a huge range of numbers using very compact notation.

The relevant floating point format is the IEEE 7544? Floating Point Format.

## Floating Point Format

There are three parts:
- Sign Bit: 0 is positive, 1 is negative
- Significant (aka the *mantissa*): Stores the 23 most significant bits after the decimal point
- Exponent: Used a [[Biased Numbers (Floating Point Exponents)|Biased Base 127 Encoding]] (store the number + 127)
	- We can represent any number from [-127, 128]

Zero is simply represented as having all zeros for the exponent bits.

The first bit is the Sign Bit
The next eight bits are the exponent bits.
The last 23 bits are the mantissa.

Since we have already decided the zero case, you'll realize that all numbers (since they're in scientific notation) will start with `1.XXX...`, or a 1 before the decimal point. Since this is true, to save space we remove this redundant information and just assume the one is there. This let's us technically have an extra bit of information to store, which is neat.



