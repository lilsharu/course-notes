---
tags:
  - eecs-370
aliases:
  - Single-Cycle Datapath
  - Single-Cycle Processor
---
Related Classes: [[EECS 370]]

Note: This is specific for the [[LC2K]] [[Instruction Set Architecture (ISA)|ISA]] (if you recall, ISAs are intrinsically linked to [[Assembly]], as well as the processor).

A single-cycle datapath means that each LC2K instruction takes a single cycle through this circuitry to run—thus the name single-cycle.

![[lc2k-single-cycle-datapath.png|"LC2K Single-Cycle Datapath"]]

There are three types of components:

- **State:** Everything in grey holds and represents state.
	- For now, we can assume that everything is stored using [[Sequential Logic#D Flip-Flop|D Flip-Flops]], even though they're actually not the most efficient way to store large data like memory.
- **Compute**: Everything in blue is combinational logic to run computations.
	- This includes [[Combinational Logic#Adders|Adders]], [[Combinational Logic#Arithmetic-Logic Units (ALUs)|ALUs]], and more
- **Control**: Everything in orange isn't *transforming* data per say, but controls the flow of information and logic through the circuitry
	- This primarily includes [[Combinational Logic#Muxes|Muxes]] and a [[Read Only Memory (ROM)|ROM]]

The biggest drawback of single cycle processors like this one is that the clock period is limited by the slowest instruction (since the clock period is a constant). This means that, even if the slowest instruction is run the fewest time, it bottlenecks every instruction. Often, the effect of this can be fixed / negated by using [[LC2K Multi-Cycle Datapath|Multi-Cycle Processors]] instead.
