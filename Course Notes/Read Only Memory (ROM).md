---
tags:
  - eecs-370
aliases:
  - ROM
  - Read Only Memory
  - ROMs
---
Relevant Classe: [[EECS 370]]

Read-Only Memory is an "array" of values that are constant and non-volatile. This means that if, for example, the power cuts off, the data is still preserved. Consider the alternative, a [[Sequential Logic#D Flip-Flop|D Flip-Flop.]] The second the power goes out, a D Flip-Flop will lose the current data it is storing: however, a ROM will not.

You can think of ROM as a table: you can have $n$ input bits, and thus $2^n$ different output combinations, based on the input bits. Thus, you might notice, that the input is turned into a single bit using a [[Combinational Logic#Decoder|Decoder]].

In addition, a ROM can have as many "output" bits as you want, and each input combination determines what the output bits are set to. Thus, the size of the ROM can be calculated as follows:

> [!example] 
If you have $n$ input bits and $y$ output bits, that means that there are $2^n$ possible "output states", and each output state has $y$ bits that it needs to set. Therefore, the size of a ROM in this configuration is $y \cdot 2^n$ bits

There are two primary types of ROMs.

## Programmable Read Only Memory

This type of ROM only gives you one chance to write to it: once it's written to, it's done and can't be written to again. Generally, these are implemented with diodes and other physical circuitry that, upon writing, is broken—limiting the amount of changes that can be made in the future.

## Electronically Erasable PROM (EEPROM)

You can write to memory electronically, but with EEPROMs you can use hardware to reset bits if you need to update the values. 