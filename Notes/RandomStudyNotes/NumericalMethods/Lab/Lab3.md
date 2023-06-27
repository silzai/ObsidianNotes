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
## Decision/if-structure
```
if blabla > 5
	do this;
elseif blabla >= 3
	do this;
else
	do this;
```



