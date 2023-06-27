#### More about plotting graphs:
- To change the attributes `color`, `shape`, and `line style`, we will add one more argument to `plot(x,y)`, to see all the options, just do `help plot`:
```
plot(x, y, 'sr-')
```

- To change `Linewidth`, `Markersize`, `MarkerEdgeColor`, `MarkerFaceColor`, will add, again we can just use `help plot` to copy/paste this code:
```
plot(x,y,'--rs','LineWidth',2,...  
	'MarkerEdgeColor','k',...  
	'MarkerFaceColor','g',...  
	'MarkerSize',10)
```

- To make multiple plots in one window, it can be used to plot different quantity graphs:
```
subplot(m, n, p)
```
- where: m is number of rows, n is number of columns, p is the plot position that will be activated. for example:
```
subplot(2, 2, [1 2]);
plot(x, y);
subplot(2, 2, 3);
plot(y, x);
// This code will make a 2x2 grid on a window and plot two graphs such that the (x, y) plot will be covering the plot positions 1 and 2, while (y, x) will cover position 3 on the window
```
## M-Files
- savable scripts that we can write for MATLAB, we have function files, and script files

### Function files:
- There are 3 parts to a function file:
	1) the keyword function
	2) the output variable
	3) name of the function
	4) the input variables in parentheses
example:
```
function outputVariable = nameOfFuntion (input1, input2, ...)
// body of funtion
end
------can omit some things from funtion signature------
function nameOfFunction
//body
end
```
- tip: comments (%) that we wrote in the function file will be given by the `help fileName` command 
- We can make function more user-friendly by asking for input using `input` and showing the output using `disp`,  for example:
```
m = input('mass (kg): ');
disp(m);
```

- For displaying multiple things instead of `disp` there is more powerful function `fprintf`, we have the following command:

```
//in a string inside the fprintf funtion:
%10.2f : this will keep 10 spaces before the number and put 2 decimal places

```