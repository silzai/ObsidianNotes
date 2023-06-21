- Problems Included:
1) 0-1 Knapsack Problem
2) Travelling Salesman Problem

- Used for optimization i.e. maximization, minimization
- Computes the `bound` at a node to determine whether it is promising
	- If `bound` is better than `bestValue`, then node is promising
# 0-1 Knapsack:

> Motivation: 
> The backtracking approach for this is very similar to the branch and bound approach, but the difference is that in backtracking, the node we explore (using depth-first search) is chosen according to the bound.
> In branch and bound approach, we will check all promising nodes in a level in the tree (using breadth-first search) and only visit the children of the node with the best bound out of them all. 
> This is faster than depth-first search, and is called "best-first search".

- Will have 3 functions in total:
	- `knapsack3()` function that does general calculation
	- `bound()` function that calculates the bound, it returns a float value
	- `promising()` function that calculates if node is promising or not
- The `promising()` function will be:
	- `bound > maxProfit`
	- `weight < totWeight`

# Travelling Salesman:

