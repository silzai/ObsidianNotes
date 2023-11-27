- ISTQB provides certification for software testing
- component testing = unit testing
- unit test = lowest level
- integration test = higher level
- system test = highest level
	- functional test
		- functional requirements test
	- quality test
		- non-functional requirements test
	- acceptance test
		- customer verifies all requirements
		- alpha testing: done on developers side
		- beta testing: done on actual audience
	- installation test
		- test done in user environment

# Cyclomatic Complexity
- Upto between 10 and 20 is good

# Coupling
- There are 5 types of coupling:
	1) sd
	2) stamp coupling
- Regular exam question:
	- We will have a graph of nodes that represent components, and directed edges with labels that represent the couple type and number of times it occurs.
- We will see 2 nodes, and a directed edge with a label that represents the coupling type and the number of times it occurs.
- The formula for calculating coupling is: $$the \ formula$$
# Information Flow Complexity
- Related to the complexity of different 
- Fan-in:
	- ingoing dependencies of a module (class/method)
- Fan-out:
	- outgoing dependencies of a module (class/method)
>[!note]
>A module with a large fan-out are expected to have a positive correlation with defect rates

## Computing "Information Flow Complexity"
- This metric was proposed by Henry & Kafura, so is called "Henry & Kafura (Information Flow) Complexity", the formula is: $$Information \ Flow \ Complexity=KLOC*(fanin*fanout)^2$$
- Where:
	- KLOC = number of lines divided by 1000
- The module with largest $Information \ Flow \ Complexity$ has the highest complexity
# System Complexity Model
- This metric is for calculating ==??==
- can be used for refactoring, more complex modules means, I need to test it more, since there are more complex, they may need to bring more bugs
- The formula is: $$C_t=S_t+D_t$$
- Where: 
	- $C_t$ = System Complexity
	- $S_t$ = structural complexity (inter-module complexity), We can talk about structural complexity of whole system: $$S_t=\frac{\sum f^2(i)}{n}$$
		- Where 
			- $f$ = fan out of 1 module
			- $n$ = number of modules
	- $D_t$ = Data Complexity (intra-module complexity), will only look at each module, then add all of the values and divide by the number of modules:  $$D_t = \frac{\sum D_i}{n}$$
		- Where:
			- $D_i$ = data complexity of ==1 MODULE== $$D_i=\frac{V(i)}{f(i)+1}$$
			- $V(i)$ = total number of input and output variables
			- $f(i)$ = fan out of module i

- Number of parameters for a function, if a module consists of several functions, then that 