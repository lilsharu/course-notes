---
tags:
  - "#eecs-281"
  - "#data-structure"
lecture: "Lecture 02: Data Structures and Abstract Data Types"
---
Relevant Classes: [[EECS 281]]

Stacks support insertion / removal in LIFO (last in, first out) order.

## [[Abstract Data Type (ADT)]]

| Method          | Description                                   |
| --------------- | --------------------------------------------- |
| `push(object)`  | Add object to the top of the stack            |
| `pop()`         | Remove top element                            |
| `object& top()` | Return a reference to the current top element |
| `size()`        | Number of elements currently in the Stack     |
| `empty()`       | Checks if the stack has no elements           |
## Examples
- Web browser's "back" feature
- Text editor's "Undo" feature
- Function calls in C++

## Implementations
### Contiguous Memory: [[Vector]]

| Method          | Implementation                                                                                                | Time Complexity                 |
| --------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------- |
| `push(object)`  | 1. If needed, allocate a bigger array and copy data<br>2. Add a new element at `top_ptr`, increment `top_ptr` | Amortized O(1), Worst-Case O(n) |
| `pop()`         | Decrement `top_ptr`                                                                                           | O(1)                            |
| `object& top()` | Dereference `top_ptr - 1`                                                                                     | O(1)                            |
| `size()`        | Substract `base_ptr` from `top_ptr` pointer                                                                   | O(1)                            |
| `empty()`       | Check if `base_ptr == top_ptr`                                                                                | O(1)                            |
### Connected Memory: [[Linked List]]

| Method          | Implementation                                    | Time Complexity |
| --------------- | ------------------------------------------------- | --------------- |
| `push(object)`  | Insert a new node at `head_ptr`, increment `size` | O(1)            |
| `pop()`         | Delete node at `head_ptr`, decrement `size`       | O(1)            |
| `object& top()` | Dereference `head_ptr`                            | O(1)            |
| `size()`        | Return `size`                                     | O(1)            |
| `empty()`       | Check if `size == 0` or `head_ptr == nullptr`     | O(1)            |