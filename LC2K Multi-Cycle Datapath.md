---
tags:
  - eecs-370
aliases:
  - Multi-Cycle Datapath
  - Multi-Cycle
  - Multi-Cycle Processor
---
Related Courses: [[EECS 370]]

The idea behind Multi-Cycle processors is that we can break instructions up into several steps, and then execute each step during a clock cycle. When doing this, now shorter instructions can take less time because they take fewer cycles.

Especially as [[Instruction Set Architecture (ISA)|ISAs]] become more complicated (think having a multiply opcode), this becomes a lot more valuable because you can have instructions that take many steps no longer holding back the performance of very simple instructions.

> Note: In [[LC2K]], you'll often notice that the performance benefit is not that large (or sometimes even negligible, if not negative). This is because all instructions are relatively tame and simple, so the overhead of a multi-cycle processor is often higher than the benefit that it offers.


![[lc2k-multi-cycle-datapath.png]]

Primary Changes from the [[LC2K Single-Cycle Datapath]]:
- Enabling / Disabling the [[Program Counter]]
- Instruction Register
	- Allows us store the current instruction without having to call from memory
- Memory is Consolidated (Proper von Neumann Architecture)
- [[Combinational Logic#Arithmetic-Logic Units (ALUs)#ALU|ALU]] [[Combinational Logic#Muxes|Mux]] Now has 0 and 1 as options as well
- ALU Result is stored

## Cycles Per Instruction

All Instructions have the same first two cycles:

- Cycle 0: Fetch Cycle
	- This involves reading from the instruction memory and storing the values fetched into the instruction register.
	- During this cycle, we also calculate `PC + 1` to use all parts of the processor because otherwise the ALU is not being used
- Cycle 1: Decode
	- This involves taking the instruction from the instruction register and loading the relevant values from the Register file (`regA`, `regB`) / pass values into the Sign Extender
	- During this cycle, we set `PC` to `PC + 1`

### Add / Nor: 4 Cycles

- Cycle 3: `add/nor`
	- Now that we've read values from the register file, we can use the ALU to `add/nor` the values together and store the result in the ALU Result Register
- Cycle 4: Store in Register File
	- After we are sure that the ALU Result Register has updated, we can use this result as the input to the register file and store it into `destReg`

### Load Word: 5 Cycles

- Cycle 3: calculate `regA + offset`
	- Now that we've read `regA` and sign-extended our destination, we can add those together to get the value in memory that we want to read to be able to store back into `regB`
- Cycle 4: read `regA + offset` from memory (get `MEM[regA + offset]`)
	- Using the ALU result, we can pass that as our source address for memory to read into the "data" register
- Cycle 5: store `MEM[regA + offset]` into `regB`
	- Now that the data from memory is calculated / stored in a register, we can store it into the register file at `regB`

### Store Word: 4 Cycles

- Cycle 3: calculate `regA + offset`
	- Now that we've read `regA` and sign-extended our destination, we can add those together to get the value in memory that we want to read to be able to store back into `regB`
	- Note: we're still going to want to read `regB` from the register file during this cycle, because that value will be used in the next cycle to write to memory
- Cycle 4: write `regB` into `MEM[regA + offset]`
	- Using these calculated values, we can write our desired value into memory

### BEQ: 4 Cycles

- Cycle 3: calculate `beq` destination (`PC + 1 + offset`)
	- Using the value of `PC + 1` currently stored in `PC` already, we can add that to the sign extended offset using the `ALU` to get the potential next destination if the equality holds
- Cycle 4: potentially update `PC`
	- Add an [[Combinational Logic#AND and OR Gate|OR Gate]] to the PC-Enable bit: either the PC enable bit is 0, or we're in State 12 (the state of this current cycle) AND the values in `regA` and `regB` are equal (changing the relevant muxes)

## Choosing Which State to Transition To

To avoid cluttering our [[Read Only Memory (ROM)|ROM]], we will use a very neat trick: the only situation in which we're unsure what state to proceed to is after the Decode State. What we can cleverly do is use one of the unused "next state" variables (here, we chose `1111` for clarity), and, if that is our next state output, we can use a mini [[Read Only Memory (ROM)|ROM]] instead that takes in the opcode and calculates the next state.

This will require the use of an [[Combinational Logic#AND and OR Gate|AND Gate]] and a [[Combinational Logic#Muxes|Mux]].

## Measuring Performance

Measuring performance of a multi-cycle datapath can be done using multiple (equivalent) formulas. Note: all of these depend on the specific distribution of instructions.

The first formula uses `CPI`, or "cycles-per instruction". This is the average number of cycles per instruction in a program. The second can easily be obtained using dimensional analysis with the first. $$T=\text{CPI} \cdot I_{\text{count}} \cdot \text{Clock Period} = \text{Cycles} \cdot \text{Clock Period}$$, where $T$ is total time and $I_{\text{count}}$ is the number of instructions in the program total.