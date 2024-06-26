---
tags:
  - eecs-370
---
Relevant Classes: [[EECS 370]]

LC2K is a "fake" (albeit Turing Complete) [[Assembly|Assembly Language]] designed by the EECS 370 staff to make learning the concepts of assembly easier (without the ridiculous number of opcodes and other functionality most real assembly languages have).

Instructions are 32 bits in size, registers are 32 bits. There are 8 registers, where register 0 is always 0. It supports $2^{16} = 65536$ words of memory (so there are only that many possible instructions and total pieces of memory).

## LC2K [[Instruction Set Architecture (ISA)|ISA]]

(Copied and Pasted from the P1 Spec)

| Assembly language name for instruction | Instruction Opcode in binary | Action                                                                                                                                                                                                                                                                                                                        |
| -------------------------------------- | ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `add`  <br>(R-type instruction)        | `0b000`                      | Add contents of `regA` with contents of `regB`, store results in `destReg`.                                                                                                                                                                                                                                                   |
| `nor`  <br>(R-type instruction)        | `0b001`                      | Nor contents of `regA` with contents of `regB`, store results in `destReg`. This is a bitwise nor; each bit is treated independently.                                                                                                                                                                                         |
| `lw`  <br>(I-type instruction)         | `0b010`                      | "Load Word"; Load `regB` from memory. Memory address is formed by adding `offsetField` with the contents of `regA`. Behavior is defined only for memory addresses in the range [0, 65535].                                                                                                                                    |
| `sw`  <br>(I-type instruction)         | `0b011`                      | "Store Word"; Store `regB` into memory. Memory address is formed by adding `offsetField` with the contents of `regA`. Behavior is defined only for memory addresses in the range [0, 65535].                                                                                                                                  |
| `beq`  <br>(I-type instruction)        | `0b100`                      | "Branch if equal" If the contents of `regA` and `regB` are the same, then branch to the address `PC+1+offsetField`, where `PC` is the address of this beq instruction.                                                                                                                                                        |
| `jalr`  <br>(J-type instruction)       | `0b101`                      | "Jump and Link Registerç; **First** store the value `PC+1` into `regB`, where `PC` is the address where this `jalr` instruction is defined. **Then** branch (set PC) to the address contained in `regA`. **Note** that this implies if `regA` and `regB`refer to the same register, the net effect will be jumping to `PC+1`. |
| `halt`  <br>(O-type instruction)       | `0b110`                      | Increment the `PC` (as with all instructions), then halt the machine (let the simulator notice that the machine halted).                                                                                                                                                                                                      |
| `noop`  <br>(O-type instruction)       | `0b111`                      | "No Operation (pronounced no op)" Do nothing.                                                                                                                                                                                                                                                                                 |
Note: above, `PC` refers to the [[Program Counter]]; and `regA`, `regB`, and `destReg` refer to [[Registers]]


| Instruction Type    | Instructions in category | Description of required fields                                                                                                                                                                                                   |
| ------------------- | ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| R-Type Instructions | `add`, `nor`             | `opcode`, `field0`, `field1`, and `field2` are required fields:  <br>`field0` is a register (regA)  <br>`field1` is a register (regB)  <br>`field2` is a register (destReg)                                                      |
| I-Type instructions | `lw`, `sw`, `beq`        | `opcode` , `field0` , `field1` and `field2` are required fields:  <br>`field0` is a register (regA)  <br>`field1` is a register (regB)  <br>`field2` is either a numeric address, or a symbolic address (represented by a label) |
| J-Type instructions | `jalr`                   | `opcode`, `field0`, and `field1` are required fields:  <br>`field0` is a register (regA)  <br>`field1` is a register (regB)                                                                                                      |
| O-Type instructions | `noop`, `halt`           | Only the `opcode` field is required                                                                                                                                                                                              |

| Instruction Type                        | Binary Representation                                                                                                                                                  |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| R-type instructions (`add`, `nor`)      | bits 24-22: `opcode`  <br>bits 21-19: `reg A`  <br>bits 18-16: `reg B`  <br>bits 15-3: `unused` (should all be 0)  <br>bits 2-0: `destReg`                             |
| I-type instructions (`lw`, `sw`, `beq`) | bits 24-22: `opcode`  <br>bits 21-19: `reg A`  <br>bits 18-16: `reg B`  <br>bits 15-0: `offsetField` (a 16-bit, 2’s complement number with a range of -32768 to 32767) |
| J-type instructions (`jalr`)            | bits 24-22: `opcode`  <br>bits 21-19: `reg A`  <br>bits 18-16: `reg B`  <br>bits 15-0: `unused` (should all be 0)                                                      |
| O-type instructions (`halt`, `noop`)    | bits 24-22: `opcode`  <br>bits 21-0: `unused` (should all be 0)                                                                                                        |

The `offsetField` above is a [[Two's Complement Numbers|Two's Complement Number]]

## Labels

Labels make assembly code easier to read and write. They let us assign labels to instructions / data (memory locations) and then use them instead of absolute memory addresses (in `beq` instructions, `lw`/`sw` instructions).