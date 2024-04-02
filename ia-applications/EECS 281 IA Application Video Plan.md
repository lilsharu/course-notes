---
tags:
  - eecs-281
---
# Topic: Disjoint Set Union and Union-Find

- Favorite Algorithm / Data Structure
- Example: we have this random graph and we want to know if a vertex $v$ is connected to another vertex $w$
	- web of "connections" of students in the University of Michigan
	- is it possible to get from person $v$ to person $w$ through mutual connections?
- How many connected components are there?
- Naive Approach: DFS/BFS Each Time
	- For each vertex, we'll need to search through all its children to see if we can find $w$

# Solution: DSU
* The inspiration is thinking about sets
* Two operations
	* `union(x, y)`
	* `find(x)`
* For this approach, think of a leadership structure
	* How do you find out if two citizens are from the same country? Check if they have the same leader
* Worst Case: $O(n)$ (but with path compression, it becomes amortized $O(\alpha(n))$. 