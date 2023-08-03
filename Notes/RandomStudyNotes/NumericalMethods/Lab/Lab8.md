- Lagrange polynomial: 
- `axis()` function will set the coordinates for the screen

- will ask for plotting graphs (interpolating) 4th and 5th order polynomials using original data on the same graph:
	- steps:
		- `p4 = polyfit(x, y, 4) and p5 = polyfit(x, y, 5)`
		- then to generate the best fit y values, will use `y4 = polyval(p4, xc)` using xc, which are points generated from the range of the original x. we can do `xc = [1 : 0.1: 10]` if the x is `x = [1 3 4 7 10]`
		- will also do the same for `y5` 5th order polynomial
		- Then we will plot 3 things, that are original data points, the 4th order, and 5th order using `plot(xc, yNum)` and using `hold on`
		- ALSO must add a `legend` to differentiate the data plots: `legend('original data', '4th order', '5th order')`

- Interpolate using built-in function: `yi = interp1(x, y, xi, 'method')`, `interp1` will return the y values(s) of x.
	- where `x` and `y` are the original data values, and `xi` is the value that we need to find the `yi` of.
	- the `method` will be replaced by: `nearest, linear, spline, pchip, cubic`
	- `linear` will only return the y that is between the range, meaning it will give error if we give x value that is outside of the original x range. 
	- `nearest` (nearest neighbor) will adjust the line of best fit by keeping the line same before and after the points.
	- `spline` is the beast (وحش), it can find for you anything, outside or inside the range for any x.