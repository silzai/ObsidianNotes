# Decision Trees (Classification):
- Big advantage of decision trees:
	- Model is interpretable, it gives the actual rules of the model, as opposed to other models that are simply black boxes
- decision trees have problem of overfitting, so will use random forests to solve this problem
# Building the Tree:
1) which feature to split on?
	- use a attribute selection measure (ASM).
	- the only difference between decision tree algorithms are ASMs.
2) the split point on each feature (decision node)?
3) when/how to stop? examples:
	1) stop when depth of tree reaches certain level
	2) when number of elements of a node reach certain number
	- note: all child nodes may not be pure (because may overfit the model if we do this)

>[!note] How to split trees?
>we split nodes using nodes that have specific property that are questions. Questions are simply features with thresholds
# metrics to see which feature to split (the Attribute Selection Measure):
- error rate (opposite of accuracy) $$error \ rate=1-max(\ P(i_1|t),\ P(i_2|t)\ )$$
	- Where $i_1$ and $i_2$ are the classes in node $t$
	- Then to see the error rate of the whole "split"/node/stump we take the weighted average of all splits ==how to weighted average==
- Gini impurity index $$Gini=1-(P(T)^2+P(Y)^2)$$
	- where $T$ and $Y$ are same as $i_1$ 
	- Then to see the Gini impurity of the whole stump/split/node, we take the weighted average of all splits ==how to weighted average==
	- note: Gini impurity is always between 0 and 0.5
- entropy: 
	- can calculate information gain
	- difference of before splitting and after splitting, so will have to maximize information gain
# Determining the split point:
- for categorical features:
	- can do multi-way split or two-way split, can see the split point here with split that is least impure (yes we will choose this also using Gini's impurity index)
- for Continuous features:
	- first sort all values
	- then make splits between pairs of all values (which is the average of the pair)
	- calculate impurity using all splits, and pick the split with least impurity
> [!note] How to finish building the tree?
> Once we have a pure node, we don't need to split that node further, and that will be the final classification

- if that node is still impure, then we will split it using decisions of other stubs

>[!important] to find a powerful feature ==????==
>to find impurity of a **classifier** node, then will use weighted average of the splits
# Decision Boundaries:
- to visualize how a decision tree actually works
- When we build a tree:
	- we take tabular dataset and convert it to tree
	- then we choose the best feature to split the tree on
	- then we choose the split point of that node
	- the splitting is actually constructing decision boundaries in the feature space
	- so basically the point is, for example with normal lines in graphs, we separate the data linearly, but using decision trees, we can make boundaries that are linearly inseparable
# Advantages
- very easy to explain to people/business people, as the decision tree actually gives/shows/visualizes the steps it took to reach that decision
