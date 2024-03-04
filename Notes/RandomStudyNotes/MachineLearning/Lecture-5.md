# Classification Model Evaluation
- After creating our ML model, we don't just ship it, we first test it. This chapter is about testing the ML model
# Contents:
1) Metrics to compare data sets
	- confusion matrix
2) Testing methods (partitioning data to test)
	- Holdout method
	- cross-validation
1) Common models face: Underfitting and overfitting:
	- to solve this, we use: Reducing model complexity
		- decision tree: tree pruning: max depth
2) Ensemble Learning:
	- we actually do this in practice
	-  build multiple models, prod class, take majority votes, this will give better predictions
		- if classification: take majority
		- if numerical: take the average of all model outputs
3) random forest:
	- bootstrapping: random selection of instances with replacement
	- 
# Metrics to compare data sets with:
- We will find the following using **confusion matrix** values:
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
		- we do this to penalize the lower number
		- combines precision and recall to 1 value
		- takes the harmonic mean (more sophisticated average) $$\text{f1-score}=\frac{2 \times (precision \times recall)}{precision + recall}$$
## Testing:
- Holdout method:
	- divide dataset (e.g. 70/30) as training and test sets
- cross-validation:
	- people may use 5 folds:
		- take data set, break it into 5 partitions (also called folds)
		- then do 5 iterations where in each iteration, we take the first fold and hide it, and the remaining folds we use for training
		- so basically, by doing this, we have tested the models using the whole data set
	- actual validation is the average of all iterations
