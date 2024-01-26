>[!info] Extra Information:
>ISTQB is an organization that provides certifications for software testing, Catal has made the slides using some of ISTQB's syllabus 
# Chapter Overview:
1. Coverage testing (4 types):
	1. Statement Coverage
	2. Branch Coverage
	3. Path Coverage
	4. Condition and Multiple Condition Coverage
2. Cyclomatic complexity
3. Morphology 
4. Coupling 
5. Information flow complexity 
6. System Complexity (it is calculate using the 2 metrics below) 
	1. Structural complexity (Intermodular Complexity) 
	2. Intramodular Data complexity

>[!warning] Information about the topics above:
>The first 2 are related to testing components (coverage testing and cyclomatic complexity), while the others are related to testing inter-component interaction or "system" complexity

>[!important] What is a component?
>A component can be any single function, or class (in case of Object Oriented Programming)

# Control Flow Graph
>[!tldr] Why Control Flow Graphs?
>- Before we start seeing white box testing techniques, first we need to see what is a control flow graph, and how it is made from code.
>- We will see this because the first two topics (all the coverage testing and cyclomatic complexity) are completely based on control flow graphs (the other techniques after these do not need it)

- As the name implies, a control flow graph shows the "Control Flow" or in other words the `if-else`, `for-while loops` statements which basically control the flow of any program.
- To easily see how it is made, see ***lecture 13, slides 9-13***
# 1) Coverage Testing
- Actual white-box testing is actually coverage testing
- but study this after reading the rest of this document 😋 
- But coverage is basically how many lines of code and other things does the program actually execute.
- See this from **Lecture 13, slide 14-28**
# 2) Cyclomatic Complexity
- To calculate cyclomatic complexity: $$V(F)=e-n+2p$$
	- Where:
		- $V(F)$ = cyclomatic number of F 
		- $e$ = number of edges,
		- $n$ = number of nodes, 
		- $p$ = number of exit nodes
- Basically this and **Lecture 13, slide 20** are the same thing
- A very nice example is given on [this link](https://www.cs.kent.edu/~jmaletic/cs33901/lectures/SoftwareMetrics.pdf) on slide 9.
	- In this link, a code is given, and a control flow graph is constructed from that code
	- then the cyclomatic complexity is found from there
- Cyclomatic complexity between 10 and 20 is good
# 3) Morphology
- It is simple really, even though I don't know much about it
- It is the shape of the overall system structure, but just see **Lecture 13, slides 35-36** for this
# 4) Coupling
- There are 5 types of coupling (and the coupling strength increases as we go down the list):
	1) data coupling
	2) stamp coupling
	3) control coupling
	4) common coupling
	5) content coupling
>[!info] Tip:
>You don't need to know what each of these do, simply look below on what we will do with these:
- Regular exam question:
	- We will have a graph of nodes that represent components,
	- and directed edges with labels that represent the couple type and number of times it occurs.
	- For example, if the label is (2,5), then this means 2 is the type of coupling (stamp coupling), and 5 is the number of times the given type of coupling occurs.
- Simply see **Lecture 13, slide 39-40** for easy representation
- The formula for calculating coupling ($c$) is: $$c(x,y)=i+\frac{n}{n+1}$$
	- Where:
		- $c(x,y)$ = is the coupling between modules x and y (these are not input values, like you see in mathematical functions)
		- $i$ = is the number of the worst coupling type between x and y
		- $n$ = number of times the $i$ (worst) coupling occurs
# 5) Information Flow Complexity
- Related to the complexity of different inter-connected components

>[!important] Before seeing computing the information flow complexity:
>- Fan-in:
-ingoing dependencies of a module (class/method)
-meaning the number of modules that call *this* module
>- Fan-out:
 -outgoing dependencies of a module (class/method)
 -meaning the number of other modules *this* component is dependent on

>[!note] Tip:
>A module with a large fan-out is expected to have a positive correlation with defect rates
## Computing "Information Flow Complexity"
- This metric was proposed by Henry & Kafura, so is called "Henry & Kafura (Information Flow) Complexity", the formula is: $$Information \ Flow \ Complexity=KLOC\times(fanin\times fanout)^2$$
- $Where:$
	- $\text{KLOC = number of lines in the function/module/program divided by 1000}$

- The module with largest $Information \ Flow \ Complexity$ has the highest complexity, and leads to a greater likelihood that integration and testing effort will also increase.
# 6) System Complexity
- This is used to calculate the complexity of the whole system 

>[!information] Why System Complexity?
>As each of these complexity values increases, the overall architectural complexity of the system also increases. This leads to a greater likelihood that integration and testing effort will also increase.

>[!Warning] more on system complexity:
>- more complex modules mean, I need to test them more, and since there are more complex, they may have more bugs
>- So, this metric is useful to see if the program needs refactoring
- The formula for system complexity: $$C_t=S_t+D_t$$
- Where: 
	- $C_t$ = System Complexity
	- $S_t$ = structural complexity (inter-module complexity), We talk about structural complexity of whole system: $$S_t=\frac{\sum f^2(i)}{n}$$
		- Where 
			- $f$ = fan-out of 1 module (we need to take sum of fanouts of all modules)
			- $n$ = number of modules
	- $D_t$ = Data Complexity (intra-module complexity), is the average of all $D_i$ (data complexity) values :  $$D_t = \frac{\sum D_i}{n}$$
		- Where:
			- $D_i$ = data complexity of ==1 MODULE== in the whole system:$$D_i=\frac{V(i)}{f(i)+1}$$
			- $V(i)$ = total number of input and output variables (sum of both)
			- $f(i)$ = fan out of module $i$
- Additionally, we can also calculate **relative system complexity**: $$ C_r=\frac{C_t}{n} $$
	- Where:
		- $C_t$ = System Complexity
		- $n$ = number of modules in the system
