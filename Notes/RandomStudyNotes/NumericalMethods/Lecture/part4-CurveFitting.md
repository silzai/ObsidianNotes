- Sometimes we do measurements, or simulations, and we get data scattered all over the place in the graph, sometimes we have complicated situations between the independent variable and the dependent variable, but we want a simple version of this that gives us quick and good results
- To do this we use curve fitting

- We will do:
	1) Least-Squares Regression: to derive a single curve that shows general trend of data
			1) Linear regression
		1) Linearization of non-linear relationships
		2) polynomial regression
		3) multiple linear regression
	2) Interpolation: estimation of what is between the points (is it curvy/straight etc)
		1) Newton polynomial
		2) Lagrange polynomial
		3) Spline interpolation

## Least-Squares Regression:
- Regression: given n data point, best fit is based on minimizing the sum of the square of the residuals. The residual or error, is for any point, the actual point minus the curve point or **actual y value − predicted y value**
- Why is it called least-squares regression? when you take the square, the residual is smaller/it reduces the error 
- any point that is outside line of best fit is called noise.
### Linear Regression:
- Simplest method of least-squares approximation is linear regression (fitting a straight line)
- We will find an equation: $$y=a_0+a_1x+e$$
- So, mathematically, we already minimized the error $e$ by putting $\frac{\partial{S_r}}{a_1}=0$ and $\frac{\partial{S_r}}{a_0}=0$, and use these to find the simple equations below, so just need to solve these equations to find the constants for line of best fit: 
- to find the constants $a_0$ and $a_1$: $$a_1=\frac{n\sum x_i y_i-\sum x_i\sum y_i}{n\sum x_i^2 - (\sum x_i)^2},\space a_0=\bar{y}-a_1\bar{x}$$
where 
- $n$ = number of pairs of points
- $\bar{y}$=average of all y
- $\bar{x}$ = average of all x

#### Error Quantification of linear regression: 
- $S_r$ is the Summation of the squares of the vertical distance between data and best fit or sum of the squares of the residuals, it is found using $y=a_0+a_1x+e$, where we make $e$ the subject: $e=y_i-a_0-a_1x$ , and so: $$S_r = \sum{e_i^2}=\sum{(y_i-a_0-a_1x_i)^2}$$
-  $S_t$, the summation of the squares of the discrepancy between data and the mean: $$S_t=\sum{(y_i-\bar{y})^2}$$
- *standard error of estimate* $S_{y/x}$, it has many uses, but we will not use it for anything besides calculating it here: $$S_{y/x}= \sqrt{\frac{S_r}{n-2}}$$
- If $r$ or correlation coefficient ($r^2$ = coefficient of determination) is close to or exactly 1 then it is most better fit, correlated well to the exact data: $$r^2=\frac{S_t-S_r}{S_t}, r = \sqrt{\frac{S_t-S_r}{S_t}}$$
- If $r=1$ and $S_r=0$ then it is a perfect fit. 

#### Linearization of non-linear relationships:
- If there is curve in the data points, then we have to consider it, otherwise line of best fit will not be useful, for this, will do linearization of nonlinear relationships. Exponential, power and saturation-growth rate models can be linearized.
- By linearizing the model, we will end up with new points, for example for a power model: $y=ax^b$, we can linearize it by taking $ln$ on both sides, so will have $ln\ y= ln\ a+ b\ ln\ x$, then we can also write the new values as: $y'=a_0+bx'$ , and do regression on this.
### Polynomial Regression:
- Some engineering data is poorly represented by a straight line. For these cases, a curve would be better suited to fit the data. 
- we have $$y = a_0 + a_1x + a_2x^2 + ... + e$$
- And again, the least-square procedure is extended to a higher-order polynomial, in this case, the second-order, and again already, it is put $\frac{\partial{S_r}}{a_1}=0$ , $\frac{\partial{S_r}}{a_0}=0$ as well as $\frac{\partial{S_r}}{a_2}=0$ to formulate a system of equations, and solve using gaussian elimination to find the coefficients of the line/curve of best fit.
- We don't need to do all of the above derivation, and just use the simple system below to find the coefficients:  $$\begin{bmatrix}n \quad \sum x_i \quad \sum x_i^2 \cr \sum x_i \quad \sum x_i^2 \quad \sum x_i^3 \cr \sum x_i^2 \quad \sum x_i^3 \quad \sum x_i^4\end{bmatrix} \begin{bmatrix} a_0 \cr a_1 \cr a_2 \end{bmatrix} = \begin{bmatrix} \sum y_i \cr \sum x_iy_i \cr \sum x_i^2y_i \end{bmatrix}$$
- We can follow the same pattern above for any higher degree polynomial, and find their coefficients.

### Multiple Linear Regression
- Here, y is a linear function of two of more independent variables
- when we solve it, we end up with a plane, not a line, 
==need to complete==

## Interpolation
Why do we need interpolation? sometimes we have a lot of data on table, we have to estimate the intermediate values between precise data points
- Most common method used for this is polynomial interpolation.
- Polynomial interpolation consists of determining the unique nth order polynomial that fits n+1 data points
- The polynomial interpolations we will use are: Newton and Lagrange polynomials
#### Newton's polynomial
- Uses finite divided differences
There are 2 ways:
- Linear interpolation: will find $y$ value between 2 $x$.
	- linear interpolation only works if we have 2 data points and we have to predict a value between them, but we cannot a value outside of the range of the data, it is simply:
	
- higher order polynomial interpolation works with the same concepts but are more accurate than linear interpolation if there is a curve.
- Will first find the coefficients $b_1, b_2, ... b_n$ step by step using: $$b_n=f[x_n, x_{n-1},...x_2,x_1]=\frac{f[x_n, x_{n-1},...x_2]-f[x_{n-1}, x_{n-2},...x_1]}{x_n-x_1}$$
- Then will use this formula to formulate the $nth$ order polynomial: $$f_n(x)=b_1 +...+b_3(x-x_1)(x-x_2)+...+\ b_{n+1}(x-x_1)(x-x_2)...(x-x_n)$$


#### Lagrange Polynomial
- Is a reformulation of Newtons polynomial that avoids computation of divided differences.
There are two ways:
	- 1st order: For linear interpolation:$$f_{1}(x)=L_1(x)f(x_1)+L_2(x)f(x_2)$$
		- Where: $L(x)$ is an equation with unknowns
		- and $f(x_i)$ is the given $y$ values
	
- 2nd order: For quadratic interpolation:
	- Same as 1st order but calculating for 3 data points, 

#### Spline Interpolation
- There are cases with polynomials that lead to errors, alternative is to use splines 
==need to complete==
- also read about quadratic splines

