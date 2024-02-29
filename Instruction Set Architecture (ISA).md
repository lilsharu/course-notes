---
tags:
  - eecs-370
aliases:
  - ISA
  - Instruction Set Architecture
---
ISAs are a is a description of what operations that a specific set of hardware will support and understand. They are platform-specific and intrinsically tied to what the hardware that it is created for.

Generally, ISAs use and depend on the following:
- [[Registers]]

## Control Flow
In an assembly program, you *almost* go line by line. There is the notion of a [[Program Counter]], or `PC`, that represents the current instruction that is being executed.

After most instructions, the `PC` is incremented, but based on the ISA, there are generally a few instructions that can change the `PC` in different ways (think function calls, branching, etc).

## Load-Store Architecture
1. **Load** data from memory into a register
2. **Calculate** things based on stored register values (compact and fast)
3. **Store** data back into memory from registers after they are done being used / calculated

## Addressing Modes
### Direct Addressing
Equivalent to "hard-coding" the address in the instruction. However, if the instruction is the same size of the address, you can't include both an address and the instruction you want to operate on that address, so it is impractical.

## Register Indirect
Store the address in a register, and use the register to access memory addresses (essentially storing an address in a variable, like a [[Pointer]]).

## Base + Displacement
Essentially, it is a combination of the above two. For example, when using a [[Struct|struct]], we know the offset of each variable from the start. Essentially, we have a register to store the address of the "base" of a variable, and we hard-code ("directly-address") the offset / displacement from the base. Think [[Array|Arrays]] or [[Struct|Structs]].

## PC-relative Addressing
This is the same as Base + Displacement, but uses the [[Program Counter]] as a base.
## Example ISAs

- [[LEGv8]]
- [[LC2K]]