- To generate random numbers, will generate a matrix with values between 0 and 1:
```
R = rand(m,n);
% m = number of rows
% n = number of columns
% to specify the range between lower and upper values, will do:
X = low + (up - low)*rand(m,n)
```
- for generating numbers with mean 0, and stdv 1:
```
randn(m,n)
% to change the mean, will do:
X = average + std*randn(m, n);
```

- To find coefficients of polynomial regression using built-in functions:
```
P = polyfit(x, y, n)
% where x and y is the data, and n is the order of polynomial
% note that this return values in descending order of coefficients
```
- To find y value using `P` and an x value:
```
y = polyval(P, x)
% P is the polyfit command variable above, and x is one input value
```

- For excel, plotting line:
	1) double click any point on chart
	2) enable trendline
	3) display equation on chart
	4) display R-squared value on chart

- For Excel multiple linear regression:
	- First put the
	1) go to: Data analysis --> regression
	2) select column y in the y input section
	3) select all x columns altogether in x input section
	4) press ok
