---
tags:
  - "#eecs-281"
  - "#data-structure"
lecture: "Lecture 2: Data Structures and Abstract Data Types"
---
Queues support insertion / removal in FIFO (first in, first out) order.

## [[Abstract Data Type (ADT)]]

| Method          | Description                                                 |
| --------------- | ----------------------------------------------------------- |
| `push(object)`  | Add object to the back of the queue                         |
| `pop()`         | Remove element at the front of the queue                    |
| `object& top()` | Return a reference to the element at the front of the queue |
| `size()`        | Number of elements currently in the queue                   |
| `empty()`       | Checks if the queue has no elements                         |
## Examples
- Lunch Line
- Adding Songs to a Playlist

## Implementations
### Contiguous Memory: [[Circular Buffer]]

| Method          | Implementation                                                                                                                                                                                                                                             | Time Complexity                 |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- |
| `push(object)`  | 1. If `size == capacity`, reallocate larger array and copy over elements, "unrolling" as you go (unroll: start front_idx at 0, insert all elements)<br>2. Insert value at `back_idx`, incrementing `size` and `back_idx`, wrapping around either as needed | Amortized O(1), Worst-Case O(n) |
| `pop()`         | Increment `front_idx`, decrement `size`                                                                                                                                                                                                                    | O(1)                            |
| `object& top()` | Return reference to element at `front_idx`                                                                                                                                                                                                                 | O(1)                            |
| `size()`        | Return `size`                                                                                                                                                                                                                                              | O(1)                            |
| `empty()`       | Check if `size == 0`                                                                                                                                                                                                                                       | O(1)                            |
### Connected Memory: [[Linked List]]

| Method          | Implementation                                     | Time Complexity |
| --------------- | -------------------------------------------------- | --------------- |
| `push(object)`  | Append node after `tail_ptr`, increment `size`     | O(1)            |
| `pop()`         | Delete node at `head_ptr`, decrement `size`        | O(1)            |
| `object& top()` | Dereference `head_ptr`                             | O(1)            |
| `size()`        | Return `size`                                      | O(1)            |
| `empty()`       | Return `head_ptr == nullptr` (or when `size == 0`) | O(1)            |
