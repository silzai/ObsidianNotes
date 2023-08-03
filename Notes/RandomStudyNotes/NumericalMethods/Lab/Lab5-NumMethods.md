## Building a function:
- When building a function file in MATLAB, we can use `nargin` to control number of arguments into the funtion i.e.
```
% nargin is the number of args passed to the function by user
if nargin < 3, error('at least 3 args required'), end
if nargin < 4, ns = 50; end
```
## Incremental Search Method:
- finds roots between brackets, with number of 

## Bisection Method:

## Newton Raphson Method:

## Roots Built-in function:
```
fzero(function, x) % where x is the initial guess
```

## Excel:
- to find roots using excel
- will use add-in that is solver
- will make title of "x=" and "f(x)"
- then write the equation under "f(x)" using the "x=" cell 
- solver: 
	- set objective: to "f(x)"
	- by  changing variable cell: "x="
	- value of: 0
	- add subject to the constraint: "f(x) = 0"
