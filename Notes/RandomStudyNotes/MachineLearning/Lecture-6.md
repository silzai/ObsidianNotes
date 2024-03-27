# kNN
## Measures:
- Distance
- Similarity Between Binary Vectors ==why is this used???==
- 
# Naïve Bayes Classifier
## Steps:
1) compute probs of classes
2) compute probs of given feature given that class
3) now, can throw away the training dataset, we dont need it since we calculated the probabilites, and we only need that
4) To avoid 0 probabilites, will do laplace correction, in which we add 1 to each numerator and $k$ which is the number of features to the denominator
5) To avoid "numerical underflow" which is the computer not being able to represent very small numbers, so to solve, will transform all the probabilities to $log$ and do summation in the formula instead of multiplying
