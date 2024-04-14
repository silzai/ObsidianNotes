# Regression
- To predict continuous values instead of categorical
# Linear Regression with one variable/univariate
- cost function is $j(w,b)$
	- where $w$ is gradient
	- and $b$ is the intercept
- will use the $MSE$ as the cost function $$MSE=j(w, b)=\frac{1}{2m}\sum_{i=1}^m(\hat{y}_i-y_i)^2$$
- goal is to produce a linear function (find gradient and intercept) that will minimize the cost function
- features being used are the $x$
- the output are the $y$
- $x^i$ means $ith$ data of the training set, we are not using subscript because it has a reserved purpose such as representing more features
## Steps:
- will use gradient descent algorithm:
	- will use $\alpha$ (learning rate) to descend towards g(x)=0, where g = gradient
- Will use iteratively find the $w$ and $b$ which have the minimum error
- so will do $$w=w-\alpha (gradient)$$ and
 $$b=b-\alpha (gradient)$$ 
 
- see `gradient_descent_one_var.py`

>[!note]
>we will always subtract $w$ and $b$ in the gradient descent algorithm because the minus is substituted automatically by addition when there is negative value
# Multiple Linear Regression

- In python, to get the number of features from `X` 
```python
number_of_features = X.shape[0]
```
- only thing that will change in python code will be, initializing `w` that was a scalar, to a vector:
```python
w = np.zeros(n_features)
```
# Polynomial Regression
- First, Take the original features `x` and add extra features to them
	- we do this by "augmenting" them by taking powers of all original features to a certain "degree" 
- Then use that new matrix and give it to the linear Regression model will learn a line
- can use `GridSearchCV` to get the best degree to set the model (basically to get lowest variance (lowest test error) )
# Practical Aspects
- regularization