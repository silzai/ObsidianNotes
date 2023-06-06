Problems included:
1) N-Queens Problem 
2) The Sum-of-Subsets
3) The m-Coloring Problem
4) The Hamiltonian Circuits Problem
5) 0-1 Knapsack Problem

> *Backtracking:*
> Doing a depth-first search of a state space tree and checking whether each node is promising, and if it is nonpromising, backtracking to the node’s parent, also called "pruning" the state space tree.

# n-Queens Problem:
- Place $n$ queens on an $n\times n$ chess board, so that no two queens threaten each other.
## Solution:
- Each level in the tree represents a row, because it is understood that no two queens will be on the same row.
- There will be 2 functions in total, `void queens(index i)` and `promising(index i)`
- There are 2 approaches, "checknode" and "expand", both use the same promising function, but different queens functions, expand is more efficient, we will show "checknode" here.
- ```promising()``` function must check whether two queens are in the same column or diagonal.
	- To check for same column: `col(i) == col(k)` where `i` and `k` are row numbers.
	- To check for same diagonal: `abs(col(i) - col(k)) == abs(i - k)` meaning if the difference of the columns and rows are the same, then they are on same diagonal.
```java
public Boolean promising(index i) { //checks node on row i against all columns 
	index k; // index of column to check i against 
	bool switch; // as soon as switch is false, then it is non-promising
	k = 1; //will start from the first column
	switch = true;
	while ((k < i) && (switch)) {
		if ((col[i] == col[k]) || (abs(col[i] - col[k] ) == i - k))
			switch = false;
		k++;
	}
	return switch;
}
```
- `queens()` will iterate over all the possibilities on the chess board:
```java
public void queens(index i) {
	index j;
	if (promising(i)) {
		if (i == n) // if base case is reached then stop and print index of columns
		   System.out.println( col[1] through col[n] );
		else {
		   for (j = 1; j <= n; j++) {
			   col[i + 1] = j;           
			   queens(i + 1);
			}
		}
	}
}
```

# Sum of Subsets Problem:
- Find all subsets of an array that sum up to an integer $W$.
## Solution:
- First sort the array in non-decreasing order.
- like nQueens, will have two functions: `sumOfSubsets(index i, int weight, int total)` and `promising(index i)`.
- `promising()` function must check the node by the following conditions:
	- $(weight + w_{(i+1)})<W$
	- $(weight + total)>W$
		- where $weight$ = total weight of all nodes up to a level $i$
		- $w_{(i+1)}$ = weight of the next node
		- $total$ = the total weight of the remaining weights.
# m-coloring Problem:

# Hamiltonian Circuit Problem:

# 0-1 Knapsack Problem:

# Complexity:
- We can not obtain efficient time complexities for our backtracking algorithms
- Therefore, we will analyze our backtracking algorithms using the Monte Carlo technique.
- This technique enables us to determine whether we can *expect* a given backtracking algorithm to be efficient for a *particular instance*.
- 