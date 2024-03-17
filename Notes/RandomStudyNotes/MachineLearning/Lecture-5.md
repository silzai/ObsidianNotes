# Classification Model Evaluation
- After creating our ML model, we don't just ship it, we first test it. This chapter is about testing the ML model
# Contents:
1) Metrics to compare data sets
	- confusion matrix
2) Testing methods (partitioning data to test)
	- Holdout method
	- cross-validation
3) Fitting the Model (overfitting and underfitting):
	- to solve this, we use: Reducing model complexity
		- decision tree: tree pruning: max depth
4) Ensemble Learning:
	- we actually do this in practice
	-  build multiple models, prod class, take majority votes, this will give better predictions
		- if classification: take majority
		- if numerical: take the average of all model outputs
5) random forest:
	- bootstrapping: random selection of instances with replacement
	- 
# 1) Metrics to compare data sets with:
- We will find the following using **confusion matrix** values, and these metrics are particularly useful for classification models, other methods have different metrics.
## Accuracy
- accuracy is **not a good metric**, as it creates ==imbalanced classes ???== 
$$accuracy=\frac{TP+TN }{Total}$$
## Precision
- it is: among the positive predictions the model has made, how many were correct?
- we focus on the 1st column of confusion matrix $$precision=\frac{TP}{TP+FP}$$
## Recall
- it is: among the positive class instances, how many has the model correctly predicted?
- we focus on 1st row of table $$recall=\frac{TP}{TP+FN}$$
>[!important] Precision or Recall, which to use?
>- when the cost of using false positive is high, will use precision to compare models
>- when the cost of using false negatives is high, will use recall to compare models
>- So it depends on the domain, on deciding whether to use precision or recall
- 
	- F1-score
		- we do this to penalize the lower number of precision and recall
		- combines precision and recall to 1 value
		- takes the harmonic mean (more sophisticated average) $$\text{f1-score}=\frac{2 \times (precision \times recall)}{precision + recall}$$
# 2) Testing Methods:
>[!Explaining What this all is:]
>Testing is taking the test set, feeding it to the model we built, and this will give the predictions, and we compare these predictions with the actual values of the testing set, which will give us a **test error**, and we use this to build a confusion matrix.
## Holdout method:
- divide dataset (e.g. 70/30) as training and test sets
## cross-validation:
- people may use 5 folds:
	- take data set, break it into 5 partitions (also called folds)
	- then do 5 iterations where in each iteration, we take the first fold and hide it, and the remaining folds we use for training and take the performance measurements
	- so basically, by doing this, we have tested the models using the whole data set
- actual validation is the average of the performance metrics of all iterations
# 3) Fitting The Model:
-  high variance:
	- test error will be very sensitive to change in the dataset
	- When we test our overfit model: we can see that slight changes in the training set will result in drastic changes in test error
- High Bias: 
	- train set will have high error (model is underfit)
- low bias means that model is ok.
- overfitting (complex model):
	- train error will be low and test error is high
	- high variance and low bias
	- feed it more data, to make it more diverse, 
	- use ensemble learning
	- it happens when the model tries to learn all the specific things in, so in short, it does not generalize the things which does not exist in the large population
- Underfitting (simple model):
	- high bias and low variance
	- increase the complexity of the model by:
		- add more features to the dataset
- Occam's razor principle:
	- if you have multiple models of similar performance, go for or prefer the simpler model
# Solutions to fitting the model:
## pruning:
- pre-pruning: 
	- we don't let the tree grow in the first place,
	- methods to stop growing:
		- enforce maximum depth of all branches
		- enforce minimum number of instance in a leaf
		- stop when the ASM is below some threshold
		- stop when node has certain percent of a class
- post-pruning: 
	- let the tree grow fully, even creating pure leaves, but prune it at the end
	- is more accurate
	- methods:
		- Reduced error pruning:
			- make a note on how many errors each branch has
			- branch with highest errors is pruned, and the whole of it is replace with the majority vote of that branch
			- we keep doing this until a branch we prune instead increases the error
## Ensemble Learning:
- There are 3 methods:
	- bagging (is abbreviation of Bootstrap AGGregating):
		- random forest is bagging algo
		- we take a subset of the dataset, do bootstrapping
		- build a model on each bootstrap, and take the performance measurements
		- then do aggregation of each performance measurement, where:
			- for classification: majority vote taken
			- for regression: average is taken
	- boosting:
		- is similar to bagging, but is done sequentially
		- we take the bad predictions where the model underperformed, those will be boosted in the next model, so the next model will focus more on the mistakes the previous model made
		- then take the weighted average of all models, where the weight is the performance of each model
	- stacking:
		- it uses heterogenous models, as opposed to the 2 above which used only one model for each model
		- for example, a decision tree, k neighbors classifier, etc. will be used that will output their predictions
		- then a last regression model will be used to aggregate the results of the previous models