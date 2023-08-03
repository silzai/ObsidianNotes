## Returning more than one value in functions
- to return more than one output, we will represent output as a vector:
```
function [avg, stdev] = stats (x)
avg = blabla;
stdev = blabla;
end
----------------then to call that function in command window, will need to assign the varibales in command window
[avg, stdev] = Ex12 ([1 2 3 4])
```
## Sub-functions
- The main function can call sub-functions within the same M-file for ease of use.
## Decision structure:
- if-structure:
```
if blabla > 5
	do this;
elseif blabla >= 3
	do this;
else
	do this;
end
```
- switch-case structure:
```
switch testexpression 
	case Value1 
		statements1 
	case Value2 
		statements2 
	Otherwise 
		Statements otherwise 
end
```
## Loop structure:
- will write for-loop using colons of range:
```
for i = 1:0.5:2 
	disp(i)
end
```
- while loop will do normally:
```
x=8 
while x>0 
	x=x-3; 
	disp(x) 
end
```

