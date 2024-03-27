# Regression
- To predict continuous values instead of categorical
# Linear Regression with one variable/univariate
- will use the $MSE$ as the cost function $$MSE=\frac{1}{2m}\sum_{i=1}^m(\hat{y}_i00-y_i)^2$$
- goal is to produce a linear function (find gradient and intercept) that will minimize the cost function
- features being used are the $x$
- the output are the $y$
- $x^i$ means $ith$ data of the training set, we are not using subscript because it has a reserved purpose such as representing more features
- To find the minimum of the MSE, will use gradient descent algorithm:
	- will use learning rate to descend towards g(x)=0
	- 