- Why we need numerical Integration and differentiation: when we have complicated functions to take integral of, we can do it numerically, an approximation, with errors, or when we have tabulated discrete data such as that of an experiment, and we don't have a function for that

- We will do:
	1) Numerical integration
		- Newton-Cotes Methods
			1) Trapezoidal Rule
			2) Simpson Rules
	2) Numerical differentiation
		1) forward difference
		2) backward difference
		3) central difference
		4) Higher order differences

## Numerical Integration: Newton-Cotes Methods
- Newton-Cotes methods are most common numerical integrations schemes
- consists of replacing complicated function or tabulated data with approximated function
- To improve the approximation, will keep increasing points
- There are 2 forms, Closed: the integration limits are known, and opened: integration extend beyond the range of data
- We will not study Opened forms in this course.
- So, in Newton-Cotes, we just replace the original function with an approximate function like this: $$I = \int{f(x)\ dx \approx \int f_n(x)\ dx}$$
- We have two methods to use this, trapezoidal and Simpsons rules:
### Trapezoidal Rule
- provides exact solution for linear function, but not for curve
- The error of the trapezoidal rule: the truncation error 
- Trapezoidal rule only be used on mostly linear functions, and not functions with too much curve, it will give tremendous error if there is non-linearity in the functions
- For more accuracy, increase number of segments in multiple-application trapezoidal rule
- The result of the derivation for trapezoidal rules: $$I=(b-a)\frac{f(a)+f(b)}{2}$$
- Then for multiple application trapezoidal rule: $$I \approx \frac{h}{2}[f(x_0)+f(x_n)+2\sum f(x_i)]$$
- Where: $h=\frac{b-a}{n}$
- when we take smaller spaces/sub intervals
### Simpsons Rule
- Use higher-order polynomial to approximate
- is more accurate than trapezoidal rule
- We have 2 rules: 1/3 rule and 3/8 rules
- ***Simpsons 1/3 rule:***
	- Uses second order Lagrange interpolating polynomial for the approximation so should have at least 3 points
	- The result of derivation for 1/3 Simpsons rule: $$I \approx (b-a) \frac{f(x_0)+4f(x_1)+f(x_2)}{6}$$
	- if given more than 3 points, will use multiple application Simpsons 1/3 rule (slide 36)
	- *limitations*:
		- but used **only** for $x$ intervals that are equispaced
		- must have odd number of points and even number of segments
- ***Simpsons 3/8 rule:***
- to use any number of segments and points, then will use this rule $$I \approx 3(b-a)\frac{f(x_0)+3f(x_1)+3f(x_2)+f(x_3)}{8}$$
- There is no multiple application for this rule

## Numerical Differentiation
- If we have tabulated data, and have no equation and want to find the differentiation of any x from that data, then need to do numerical differentiation
- For numerical differentiation, will use 3 ways:
	1) Forward divided difference
	2) Backward divided difference
	3) central divided difference: most accurate

#### Forward Divided Difference
- We use the formula: $$\frac{df(x)}{dx}=\frac{f(x_{i+1})-f(x_i)}{h}$$
- 2nd derivative for this is:
	
#### Backward Divided Difference
- We use the formula: $$\frac{df(x)}{dx}=\frac{f(x_i)-f(x_{i-1})}{h}$$
- 2nd derivative for this is:

#### Central Divided Difference
- We use the formula $$\frac{df(x)}{dx}=\frac{f(x_{i+1})-f(x_{i-1})}{2h}$$
- 2nd derivative for this is:

#### Higher Order difference
- Higher Order difference means using more points, for example for backward difference, we will use 3 points for second order, $x_i$, $x_{i-1}$, $x_{i-2}$, similarly, we will use 4 points for central difference.