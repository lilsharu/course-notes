---
tags:
  - eecs-281
  - data-structure
lecture: "Lecture 2: Data Structures and Abstract Data Types"
---
In a Priority Queue (colloquially referred to as a `pq`), each "datum" is paired with a priority value. For example, it could be the value of the data point itself in a priority queue of numbers. A PQ supports insertion of data, and inspection (which involves "looking" at the datum with highest priority).

Note: Priority Queues are [[Customizable Containers]]. You can change the "comparator" used to determine the priority (min-pq, max-pq, custom-pq).

## [[Abstract Data Type (ADT)]]

| Method                | Description                                        |
| --------------------- | -------------------------------------------------- |
| `push(object)`        | Add object to the priority queue                   |
| `pop()`               | Remove element with the highest priority           |
| `const object& top()` | Return a reference to the highest priority element |
| `size()`              | Number of elements currently in the priority queue |
| `empty()`             | Checks if the priority queue has no elements       |
## Examples
- Emergency Call Centers:
	- Operators receive calls and assign levels of urgency
	- Lower numbers indicate more urgent calls
	- Calls are dispatched to police squads based on urgency
- Hospital queue for arriving patients
- Load Balancing for Servers

## Time Complexity

|                                                          | Insert      | Remove      |
| -------------------------------------------------------- | ----------- | ----------- |
| Unordered Sequence Container                             | Constant    | Linear      |
| Sorted Sequence Container                                | Linear      | Constant    |
| Binary Heap                                              | Logarithmic | Logarithmic |
| Array of Linked Lists (for priorities of small integers) | Constant    | Constant    |
