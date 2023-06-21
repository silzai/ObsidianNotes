- Semi colons have 3 roles:
	1) adding a semicolon after a command will do the operation but not print it.
	2) adding a semicolon inside a vector will add new rows
	3) defining multiple variables in one line

- use of colons:
	- will give range of numbers as a row vector e.g. `1 : 10`
	- can also give "step" to colon operator e.g. `1 : 0.5 : 10`, this will list the range by steps of 0.5, can also use negative step, e.g. `10 : -0.5 : 0`

- `linspace` Is similar to colon operator:
	- `linspace(0,1,6)` will list numbers from 0 to 1, divided into 6 pieces.
	- but better to use colon operator

- Whenever there is a "dot" before multiplication, division, or power, it will apply that operator on elements specifically, element by element, individually.

#### Plot:
- To make a plot, for two variables on x and y axis **with labels, title and a grid**, then the function will be:
```
plot(t,v)
xlabel('x-axis label (unit)')
ylabel('y-axis label (unit)')
title('title')
grid
```
- and then if we want to add another graph in the **same** plot.
```
(previous code for first graph...)
hold on
plot(y,x)
// typing 'hold off' will clear the previous plots and make new one
```

I wrote only this much for lab1, you can research the rest urself ¯\_(ツ)_/¯