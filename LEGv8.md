---
tags:
  - eecs-370
---
Related Classes: [[EECS 370]]

LEGv8 is a subset of the ARMv8 ISA. It is simplified to make it easier to learn and understand in a classroom environment.

It has 32 registers (`X0`-`X31`) and 64 bits in each register.

Some registers have special uses: `X31` is always 0 (also called `XZR`)

LEG is addressable

## ARM Instruction Set
1. Arithmetic
	- Add
	- Subtract
2. Data Transfer
	- Loads and Stores—LDUR (load unscaled register), STUR, etc
3. Logical
	- AND, ORR, EOR, etc.
	- Logical Shifts (LSL, LSR)
4. Conditional Branch
	- CBZ, CBNZ, B.cond
5. Unconditional Branch (jumps)
	- B, BR, BL

## Arithmetic Instructions (R Instructions)
Format: 3 Operand Fields
- **Destination Register is the FIRST ONE**
- `ADD X3, X4, X7 // X3 = X4 + X7`

Encoding given `R[Rd] = R[Rn] + R[Rm]` (in the add case):
- `opcode`: 11 bits
- `Rm`: 5 bits
- `shamt`: 6 bits
- `Rn`: 5 bits
- `Rd`: 5 bits

## LEGv8 Logical Instructions
- Logical operations are bit-wise
- For immediate fields, the 12 bit constant is padded with zeros to the left

### LEGv8 Shift Logical Instructions

## Pseudo-Instructions
- Instructions that use a shorthand "mnemonic" that expands to pre-existing assembly instructions
- Examples:
	- `MOV X12, X2 // copy X2 into X12` => `ORR X12, XZR, X2`
	- `MOVZ X12, #23 // set X12 to be 23` => `ORRI X12, XZR, #23`

## Memory Instructions
Unlike [[LC2K]], which is *word* addressable, ARM (and most modern [[Instruction Set Architecture (ISA)|ISAs]]) is ***byte*** addressable. Recall that a word is four bytes.

Just like [[LC2K]], ARM uses a base + displacement mode. However, in ARM, you can transfer different sizes (instead of the whole 64 bit value). This way, it lets us deal with non-64 bit values.

### Loads
When we're loading smaller elements from memory, there are two options on what to do with the other bits:
- Set them to zero, or *zero-extend*
- Sign-extend (extend based on the most significant bit)
ARM has different instructions for each option so the processor knows what to do.

| Desired amount of data to transfer                  | Operation                       | Unused bits in register                                |
| --------------------------------------------------- | ------------------------------- | ------------------------------------------------------ |
| 64-bits (double word, or whole register)            | `LDUR`                          | N/A                                                    |
| 16-bits (half-word) into the lower bits of register | `LDURH`                         | Set to zero                                            |
| 8-bits (byte) into lower bits of register           | `LDURB`                         | Set to zero                                            |
| 32-bits (word) into lower bits of register          | `LDURSW` (load **signed** word) | Sign extend (0 or 1 based on the most significant bit) |

### Stores
For stores, signedness doesn't actually matter: you're storing exactly what you said, there's no extension necessary (or even relevant).

| Desired amount of data to transfer                  | Operation |
| --------------------------------------------------- | --------- |
| 64-bits (double word, or whole register)            | `STUR`    |
| 16-bits (half-word) into the lower bits of register | `STURH`   |
| 8-bits (byte) into lower bits of register           | `STURB`   |
| 32-bits (word) into lower bits of register          | `STURW`   |