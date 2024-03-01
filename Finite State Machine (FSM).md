---
tags:
  - eecs-370
aliases:
  - Finite State Machine
  - FSM
---
Relevant Classes: [[EECS 370]]

A finite state machine is exactly what it sounds like: a state machine with a finite number of states, with multiple inputs that change what the next state is and the output is.'

Generally, to store the current state, an FSM uses [[Sequential Logic#D Flip-Flop|D Flip-Flops]] to store the current state, and they often use a [[Read Only Memory (ROM)|ROM]] to determine the transition function (output to the next state). 

There are two types of FSMs: Moore Machines and Mealy Machines. These terms help describe what the output is based on.

## Moore Machines

In Moore Machines, the output of the Machine is solely dependent on the current state. These are often associated with more states, because based on the input, you might need to have a different output. Therefore, instead of having one state with the output depending on how you got to that state, you have a different state for each path to the next state.

## Mealy Machines

Mealy machines are the opposite: their output is dependent on the current state, and the last input. Contrarily to Moore Machines, the input at a certain point, plus the current state, can determine what the output would be. This often leads to slightly more complicated circuits, but fewer states.

## Implementing an FSM using ROM

Designing a custom circuit can be done using gates, but that can get very financially straining (especially for something small). The alternative is to use memory:

- The entire program can be seen as a very large truth table: the current state, input bits, and then the output / next state.
- With this in mind, we can literally just store all the possible combinations of states and inputs in memory and "index" into it—which would be cheaper and more efficient. These tables are called, [[Read Only Memory (ROM)|Read Only Memory, or ROMs]].

### Basic Limitations

Let's do some math here. If we recall how to calculate [[Read Only Memory (ROM)|ROM]] sizes, $n$ input bits and $y$ output bits gives us a size of $2^n \cdot y$, which grows exponentially with regard to the input size. This means that each additional input state, the size requirement doubles, which can become very costly. Therefore, there comes a point where—if the number of inputs is large enough—a ROM might not be the best option, and instead you can use [[Combinational Logic]].

### Optimizations

Often, the optimizations involve reducing the number of input bits, and then doing some post-processing using combination logic (essentially combining memory with combinational logic). This is because combinational logic does not grow exponentially with input size, and thus can reduce our complexity by a very large margin.