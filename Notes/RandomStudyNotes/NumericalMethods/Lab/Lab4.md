## Errors:
```
error('invalid value') %will show error message, used in decision structure 
```
## Anonymous Function:
- It is a mathematical function, not to be confused with computer science functions that we studied in Lab2
- has minimum one variable, but no max
- structure:
```
f1 = @(x) x.^2;
```
- note: regarding the "dot" while multiplying or dividing power, we will do this whenever a vector is operated upon by another vector, no need if a vector is operated upon by constant.
## fplot:
- is more easier than normal plot as it takes anonymous function and range of x values as inputs:
```
fplot(f1, [2,3]) %this means that plot f1 from x=2 to x=3
```
- need to also label the root using "text arrow" by going to "insert" in the tabs section.
