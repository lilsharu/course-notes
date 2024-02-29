---
tags:
  - eecs-281
  - data-structure
lecture: "Lecture 02: Data Structures and Abstract Data Types"
---
Relevant Classes: [[EECS 281]]

A Deque is a "Double-Ended Queue," but is essentially a Data Structure that supports both [[Queue]]-like and [[Stack]]-like behavior.

It has six major methods to support these behaviors:
- `push_front(object)`
- `pop_front()`
- `object& front()`
- `push_back(object)`
- `pop_back()`
- `object& back()`

Uniquely, you can traverse the `stl::deque` with an iterator and *it allows random access of elements in constant time* (though slower than a [[Vector]])

Implementations:
- [[Circular Buffer]]
- [[Doubly-Linked List]]