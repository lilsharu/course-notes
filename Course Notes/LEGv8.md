---
tags:
  - eecs-370
aliases:
  - ARM
---
Related Classes: [[EECS 370]]

LEGv8 is a subset of the ARMv8 ISA. It is simplified to make it easier to learn and understand in a classroom environment.

It has 32 registers (`X0`-`X31`) and 64 bits in each register.

Some registers have special uses: `X31` is always 0 (also called `XZR`)

LEG is byte addressable

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

## Sequencing Instructions (Control Flow Instructions)

Sequencing Instructions change the flow of instructions that are executed. This is achieved by modifying the program counter (PC).

### Conditional Instructions

#### Type 1: Compare to Zero

The first type of Conditional Instruction is comparing to zero, and then branching. This includes `CBZ` and `CBNZ`.

| Instruction | Example       | What it does                                                                                                                                     |
| ----------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| `CBZ`       | `CBZ X1, 25`  | If the value in the specified register equals zero, then adjust the program counter by that many lines (multiply by four to get number of bytes) |
| `CBNZ`      | `CBNZ X1, 25` | If the value in the specified register does not equal zero, then adjust the PC...                                                                |
### Type 2: Program Status Register (non-zero equality comparisons)

Sometimes, you want to do comparisons that are not just equal to zero. For example, `a > b`, or `a = b` where `b` is a variable, etc. ARM allows us to this with with flags.

The flags used in ARM for this are `NZVC`, or Negative, Zero, oVerflow, and Carry. If you run an instruction that also sets a flag, this can then be referenced in a subsequent branch instruction (reference `ADDS`, `SUBS`, anything that ends in `S`).

For [[EECS 370]], we'll focus on N and Z.

While you can use arithmetic operations to set flags (which can save on lines of assembly), the most common way to set a flag is to use the `CMP` pseudo-instruction. This updates all the flags to allow you to use the correct type of branching.

## C to Assembly

When converting C code to LEG code, there are few important things that you need to keep in mind:
- At least for [[EECS 370]], exams will include doing operations on values that a certain size, and then storing them into items of another size. Being careful about the sizes is important

### Example Conversion 1

C Code:
```c
struct {int a; unsigned char b, c; } y;
y.a = y.b + y.c; // NOTE: a is an integer (32 bits), while b and c are bytes (4 bits)
```

Assembly
```assembly
/* Assume that a pointer to y is in X1 */
LDURB X2, [X1, #4] ; it starts 4 bytes after the start of the struct
LDURB X3, [X1, #5]
ADD X4, X2, X3
STURW X4, [X1, #0] ; STURW stores four bytes, or a single word
```

### Memory Alignment

When dealing with a variables in C or C++, we often need to include padding between data members to make sure things are properly aligned (to help modern hardware access things quickly and efficiently).

This means that, even though a struct looks like it only is using, say, 7 bytes of data, it might under the hood actually be using 12 bytes because of alignment.

Modern ISAs enforce the following requirement: an $n$-byte variable must start at an address $A$ such that $A \bmod{n} = 0$. This is called the "Golden Rule of Alignment"

#### Memory Alignment Example

Say we have the following C Code:

```c
char   c;
short  s;
int    i;
```

The following memory layout would be created

| `0x1000` | `0x1001` | `0x1002` | `0x1003` | `0x1004` | `0x1005` | `0x1006` | `0x1007` |
| -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- |
| `[c]`    | PADDING  | `[s]`    | `[s]`    | `[i]`    | `[i]`    | `[i]`    | `[i]`    |

So this ends up being eight bytes long. If the compiler can not change the order of fields, and the `short` and `int` declarations were swapped, this same "structure" would take 10 bytes of memory instead.

### Aligning Arrays

We treat arrays like they're just multiple of the original type, and align the start of the array accordingly.

### Aligning Structs

Structs start to break things. Specifically, in the case where you have an array of structs. Following the above procedure, we'd end up with different padding gaps between different structs, which makes it very difficult (if not impossible) to be able to navigate within the array.

This requires an addition to the golden rule: identify the largest primitive field, and ensure that the starting address of the overall struct is aligned based on that largest field (and add padding to the back so that the total size is a multiple of the largest primitive).

### Example Conversion 2: Branching

C Code
```c
int x, y; // assume x is in X1, y is in X2
if (x == y)
	x++;
else
	y++;
```

Assembly Code
```assembly
	CMP X1, X2
	B.EQ if
else:
	ADD X2, X2, #1
	B end ; unconditionally branch to end
if:
	ADD X1, X1, #1 ; the # symbol makes it so that you don't need to specify ADDI
end:
```

Also Valid Assembly Code
```assembly
	CMP X1, X2
	B.NEQ else
if:
	ADD X1, X1, #1
	B end
else:
	ADD X2, X2, #1
end:
```
### Example Conversion 3: Loops

C Code
```c
// assume all vraibles are long lon integers (8 bytes, 64 bits)
// i is in X1, start of a is at address 100, and sum is in X2
sum = 0;
for (i = 0; i < 10; i++) {
	if (a[i] >= 0) {
		sum += a[i];
	}
}
```

Assembly Code:
```assembly
	MOVZ X2, #0 ; set sum to zero
	MOVZ X1, #0
start:
	CMPI X1, #10 ; compare i to 10
	B.GE end
	LSL X3, X1, #3 ; we need to increment by eight bytes
	LDUR X3, [X3, #100] ; load the current value of a[i]
	CMPI X3, #0
	B.LT elseif ; if it's not geq 0, then continue
	ADD X2, X2, X3 ; add value to sum
elseif:
	ADD X1, X1, #1 ; increment i
	B start ; start from start
end:
```

## Function Calls

Sometimes, function calls can be very far away: more than the $2^{19}$ instructions that a typical `CBZ` or `CBNZ` branching instruction might take. This is where unconditional branching comes into play, to let us unconditionally go to far locations.

Since unconditional branches are, well, *unconditional*, no other registers need to be specified, so they allow us to specify an address up to *26* bits away, which is more than 64 million instructions. This should be plenty.

There are three types of unconditional branches in the LEGv8 ISA:

- Branch: `B`
	- Syntax: `B #OFFSET` -> go to `PC + 4 * OFFSET` (byte addressable)
- Branch to Register: `BR`
	- Syntax: `BR X30` (or any other register) -> go to the address stored in that register
- Branch with link: `BL`
	- This is commonly used in function calls
	- `BL #OFFSET` -> Store PC + 4 into `X30` and go to `PC + 4 * OFFSET`

### The Call Stack

In many situations, functions might be "passed in" data that is more than can fit in however many registers can be used to get data passed in. There needs to be a temporary place to store these values when they get passed to the function: the solution is the calls stack.

Think of the call stack as a stack of scratch paper: you can add more on top and use it and scribble things on top of it, but it is really all just temporary. When you're done with a piece of paper, you can throw it out, shred it, and eliminate any trace that it was actually there.

Every time we call a function, a **stack frame** is allocated for that function, and then discarded when that function is complete.