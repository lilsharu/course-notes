---
tags:
  - game-theory
---
Relevant Course: [[Game Theory]]

# Key Ingredients

There are a few key ingredients in a game:

- **Players:** who are the decision makers?
	- e.g. People, Governments, Companies, Employees
	- Who is controlling the outcome of the game
- **Actions:** what can the players do?
	- e.g. Enter a bid at an auction, decide whether to strike, what move to make in chess, call a raise, etc.
- **Payoffs:** what motivates the players? (why is this game even being played in the first place)
	- e.g. Profit, Relationships, Clout, etc.

# Representing Games

## Normal Form
**Also Known As:** Matrix Form, Strategic Form
* Lists what payoffs players get as a function of their actions
	* It behaves *as if* players "moved" simultaneously
	* Strategies can still encode many things
		* not constrained to single-dimensional or binary strategies

### Normal Form Representation / Factors
* Finite, $n$-person normal form game: $\langle N, A, u\rangle$:
	* **Players**: $N = \mathbb{N}_{\leq n} = \{1, \ldots, n\}$ is a finite set of $n$, indexed by $i$
	* **Action Set** for player $i$ is $A_i$:
		* $a = (a_1, \ldots, a_n) \in A = A_1 \times \cdots \times A_n$ is an **action profile**
	* **Utility Function** or **Payoff Function** for player $i$: $u_i : A \mapsto \mathbb{R}$
		* $u = (u_1, \ldots, u_n)$ is a profile of **utility functions**
		* Essentially, assigning a value or payoff to each action $a \in A$ in the action set for each individual
## Extensive Form
* Players move sequentially (often represented as a tree)
	* e.g. Chess, Checkers
		* Chess: First white player moves, then Black gets a chance to see how White moved and then react
* Keeps track of what each player knows when he or she makes each decision
	* Poker: bet sequentially—player only knows what they have, what's on the table, and what was bet

### Extensive Form Factors
* **Timing:** in what order do things happen?
* **Information:** what do players know when they act?