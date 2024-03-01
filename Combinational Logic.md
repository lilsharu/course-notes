---
tags:
  - eecs-370
---
Relevant Class: [[EECS 370]]

Combinational Logic allows us to do things with the binary that we have created.

## Transistors

Transistors can essentially be viewed as an electronic switch. High Voltage turns the transistor `on`, while a low voltage can turn it `off` (`on` means it acts like a wire, `off` means it acts like there's a break)

## Logic Gates

Logic Gates are an essential way for us to represent how we handle and deal with the data we're given (they all also have hardware counterparts). For example, if we want to do an `and` command, there is a logic gate that we can implement to do that at the bit level, which we can extend to larger binary numbers.

### Inverter

The inverter is a really basic logic gate that simply takes in an input bit and inverts it.

Here is its Truth Table:

| Input | Output |
| ----- | ------ |
| 1     | 0      |
| 0     | 1      |

### AND and OR Gate

It's an AND and OR gate...

### NAND Gate

Conceptually, a NAND gate is simply an AND gate with an inverter afterwards.

### XOR (eXclusive OR)

Like an OR gate, but both can't be true at the same time.

### XNOR Gate

Simply an Inverted XOR Gate (requires the two bits to be equal)

## Muxes

A Mux allows us to take many inputs and choose one output.

Muxes are built off of Logic Gates.

## Decoder

It takes an $N$-bit binary number and spits out $2^N$ bits, exactly one of which will be high (essentially spitting out $2^i$ where $i$ is an $N$-bit binary number).

These allow us to index into things, like a register file.

## Adders

It takes in two binary numbers an adds them together. The most common implementation of this is a chain of [[Full-Adder Circuit|Full-Adder Circuits]], and one such example of this chain is called a [[Ripple Carry Adder]]. Note: a Ripple Carry Adder is not the most efficient and not used often in hardware because you have to wait for each calculation to propagate through all the Full-Adder Circuits; however, it is a good example to look at even though it is not used in practice.

### Subtraction

Recall that `A - B = A + (-B) = A + (~B + 1)`, so we can just add `1` to the original carry bit, negate `B`, and end up able to use the same circuit logic to perform our addition.

## Arithmetic-Logic Units (ALUs)

The basic ALU for LC2K is a simple Logical Unit that combines a 32-bit NOR Gate and a Ripple Carry Adder, with a selection bit to allow choosing between the two.

## Propagation Delay

While we often act like, as soon as a gate's input change, the gate's output changes. However, that is not exactly true (for various reasons, like electrons, speed of light, transistors requiring a build-up of electrons, etc). For simplicity, we'll just consider the result: a delay between when inputs change and when an output actually ends up reacting to the change in inputs. This delay is called the Propagation Delay.

When considering a circuit that has multiple possible data paths, we refer to the delay of the circuit being the delay of the longest data path. This is because generally, based on the inputs, all data paths could be taken, so we need to be able to accommodate all possible flows of information (we will ignore the case of a circuit having a useless datapath whose value is never used, because the answer then depends on the person who is asking the question).
