- We want to learn solutions directly from the data, we can do:
- supervised learning:
	- We provide training data, and the algorithms takes "features" of the data and learns from it.
- unsupervised learning:
	- clustering: 
- self-supervised learning:
	- Have the data, but not the label, so will extract the labels automatically
- semi-supervised learning: 
	- have part of the labels, not all, so will extract them
- Feature Engineering:
- deep learning:
	- has neural networks
	- end to end training, no need for feature engineering
	- has input and output labels
	- model will keep adjusting its parameters until loss is lessened
	- features are implicitly learned
# Data Mining:
- extracting knowledge from databases
- extracts hidden patterns that we consider useful
>[!note]
>The discovery of new information in terms of patterns or rules from vast amounts of data

- We can apply data mining to the data in a data warehouse, so proper construction of the data warehouse is important for data mining

# Knowledge Discovery in Databases (KDD)
- Data mining is actually one step of a larger process known as knowledge discovery in databases (KDD)
- First get the data, and clean it/arrange it/make it to a homogenous format
- Goals:
	1) Prediction
		1) ex. may predict how a certain company may perform in stock market
	2) Identification
		1) ex. among a population, will identify if there is a disease
	3) Classification
		1) give an item a label
		2) ex. giving labels such as high risk/low risk to individuals that take a loan
# Types of KDD:
## Association rule:
- generate rules from market-basket data
- used in commercial/medical data
- any association that has association greater than minimum support and confidence, then that association is interesting (it is useful)
- good pattern has high support and high confidence
- To calculate support:
- To calculate confidence:

- To apply the association rule on databases, we use the Apriori algorithm:
- Apriori algorithm, items should have minimum support as well as minimum confidence:
	- To calculate support:
	- We have a variable "minimum support" ($sup_{min}$)
	- We have an item set and $sup$ table
	- first scan the table to get frequent items of length 1 ($C_1$)
	- in the first scan of $C_1$, we remove the items that have $sup < sup_{min}$ and store them in $L_1$ (Large item sets of length 1)
	- To calculate confidence:
	- 
- (disadvantage) We need to scan the database multiple times 
## Classification hierarchies
- classification is already a prevalent task in our life
- Process of learning a model that is able to describe different classes of data
- different classes = labels
- it is supervised learning, so need the data and labels.
>[!note] Supervised Learning
>model learns from the data
- data is 2 types here:
	- training data: to train model
	- testing data: to test the model

- practical applications: 
	- credit/loan approval by banks
	- if there is a label for a tumor, can see whether it is cancer or not
- The data could be tabular, textual, audio or video
- In our case, will use tabular data
- The table/data has features
### Training phase:
- Model construction:
1) training data is passed to classification algorithm
2) model could be based on:
	1) trees
	2) Bayesian classifier
	3) etc.
- We will do only Bayes theorem, which is: $$P(H|X)=\frac{P(H|X)}{P(X)}$$
- This model will learn a set of probabilities from sets of classes
- We will use naïve Bayes: we assume that the attributes that make that data are independent of each other.
- We will assume that the data follows a gaussian/normal distribution to calculate the probabilities
- class ($C_i$): it is a output/value of the column/feature
- To build a naïve Bayes classifier that takes tabular data:
	1) calculate probabilities of all the classes
	2) Then for every feature, calculate the probability for the class given that feature
	3) Then to make a prediction for $X$ where $X=\text{every feature that we want to predict the class for}$, for example: $X=\text{(age<=30, income = medium, student = yes)}$
	4) We will calculate $P(X|C_i)$, where $X=\text{product of all the probabilites of the features in X (that we calculated before)}$
	5) Then, we will multiple that with the class weight, $P(X|C_i) \times P(C_i)$
- Naïve Bayes gives good results, but can improve by using Bayesian networks which will measure the interdependence of the features that naïve Bayesian does not do
- naïve Bayes disadvantage:
	- Zero probability problem (if we multiply the probability of features with a feature that has 0, then result will be 0): to solve it, we use smoothing techniques (such as Laplacian correction)
## How to test the accuracy of the model?
- We can use classifier evaluation metrics: Using the confusion matrix

| Actual class | C_1            | not C_1         |
| ------------ | -------------- | --------------- |
| C_1          | True Positives  | False Negatives |
| not C_1      | False Positives | True Negatives  |
- Here, the columns C_1 and not C_2 are columns predicted by the model
- Then we will use the confusion matrix by counting the number of times these value occur and write them in the confusion matrix, using these values, we can calculate the accuracy, error rate, sensitivity (precision), specificity of the model
- ==slide 36==
### Testing phase:
- Using model in prediction

## sequential patterns
- patterns with time series:
	- can record stock prices per time
## clustering:
- unsupervised learning from data without classes/labels
- will divide a population into groups, and members of the same group will be very similar
- Uses K-means clustering (where k is the number of groups)
- Goal is to:
	- minimize inter-similarity between groups
	- maximize intra-similarity between groups
- Algorithm:
	- If suppose k=2, then I will make 2 means, with any arbitrary initialization (the mean doesn't have to be correct)
	- We are on a cartesian plane, we measure the distance between the 2 means and the data point
	- The data set will be assigned to the group of the mean with least distance
	- After going through all data points will repeat, the same as above, but replacing the 2 means with the mean of the previous iterations group
	- 