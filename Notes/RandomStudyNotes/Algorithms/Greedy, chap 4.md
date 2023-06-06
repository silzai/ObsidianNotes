- Problems Included:
- Minimum Spanning Tree
- Shortest Path (Dijkstra)
- Scheduling and Scheduling with deadlines
- Huffman code
- Fractional Knapsack (0-1 knapsack is done using dynamic programming or backtracking/branch and bound)
# Minimum Spanning Tree:
- There are 2 approaches:
	- Prim's Algorithm
	- Kruskal's Algorithm
## Prim's Algorithm:
- finding minimum spanning tree by starting at a vertex and then choosing a shortest edge to another from there
- We have the sets:
	- `activeEdges` = minimum priority queue that contains edges of vertices that are adjacent to the explored vertices
	- `relaxedVertices` = vertices that are relaxed/the answer vertex set
	- `relaxedEdges` = edges that are relaxed/the answer edge set
1) Every time we are on a vertex, we will add the vertex's edges to the set of `activeEdges` priority queue.
2) Then in the next step we add the vertex of the minimum edge from priority queue to the set of `relaxedVertices` and `relaxedEdges`.
	- After adding to the set of `relaxedEdges/Vertices` we will remove from `activeEdges` the other vertex with bigger weight that was also connected to the explorable vertex.  
3) Then we will add the adjacent edges of the new/relaxed vertex to the set of `activeEdges`.
4) repeat steps 1 to 3 until minimum spanning tree is complete or we can say that the `activeEdges` priority queue is empty.
- **Complexity:**
	- $\theta(n^2)$ 
	- It runs better on dense graphs
## Kruskal's Algorithm:
- finding minimum spanning tree by looking at all edges first and then arranging them a;sldfkjalsjdfasdlkfjalskdjf
- **Complexity:**
	- $\theta(n^2logn)$
	- It runs better on sparse graphs

# Dijkstra's Algorithm:
- We will start from any 
- Complexity: 
	- $\theta(n^2)$ 

# Scheduling:
- Complexity : 
	- for problem of minimizing total time in the system: $\theta(nlog n)$ 
	- for problem of deadlines: $\Theta(n^2)$ 

# Huffman coding:
- Complexity:
	- $O(n  log n)$ 